---
title: Tworzenie kontrolki korzystającej z funkcji czasu projektowania programu Visual Studio
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms controls, creating
- design-time functionality [Windows Forms], Windows Forms
- DocumentDesigner class [Windows Forms]
- walkthroughs [Windows Forms], controls
ms.assetid: 6f487c59-cb38-4afa-ad2e-95edacb1d626
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7166b4203c54ab31f1d929c85cf1e6481ff120f8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744077"
---
# <a name="walkthrough-create-a-control-that-takes-advantage-of-design-time-features"></a><span data-ttu-id="f60b6-102">Przewodnik: Tworzenie kontrolki korzystającej z funkcji czasu projektowania</span><span class="sxs-lookup"><span data-stu-id="f60b6-102">Walkthrough: Create a control that takes advantage of design-time features</span></span>

<span data-ttu-id="f60b6-103">Środowisko czasu projektowania dla kontrolki niestandardowej można rozszerzyć przez tworzenie skojarzonego projektanta niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="f60b6-103">The design-time experience for a custom control can be enhanced by authoring an associated custom designer.</span></span>

<span data-ttu-id="f60b6-104">W tym artykule przedstawiono sposób tworzenia niestandardowego projektanta dla kontrolki niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="f60b6-104">This article illustrates how to create a custom designer for a custom control.</span></span> <span data-ttu-id="f60b6-105">Zaimplementowano typ `MarqueeControl` i skojarzoną klasę projektanta o nazwie `MarqueeControlRootDesigner`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-105">You'll implement a `MarqueeControl` type and an associated designer class called `MarqueeControlRootDesigner`.</span></span>

<span data-ttu-id="f60b6-106">Typ `MarqueeControl` implementuje widok podobny do neonu, animowany sygnalizator i migający tekst.</span><span class="sxs-lookup"><span data-stu-id="f60b6-106">The `MarqueeControl` type implements a display similar to a theater marquee with animated lights and flashing text.</span></span>

<span data-ttu-id="f60b6-107">Projektant tej kontrolki współdziała z środowiskiem projektowym w celu zapewnienia niestandardowego środowiska czasu projektowania.</span><span class="sxs-lookup"><span data-stu-id="f60b6-107">The designer for this control interacts with the design environment to provide a custom design-time experience.</span></span> <span data-ttu-id="f60b6-108">Za pomocą projektanta niestandardowego można utworzyć niestandardową implementację `MarqueeControl` z animowanymi sygnalizatorami i migającym tekstem w wielu kombinacjach.</span><span class="sxs-lookup"><span data-stu-id="f60b6-108">With the custom designer, you can assemble a custom `MarqueeControl` implementation with animated lights and flashing text in many combinations.</span></span> <span data-ttu-id="f60b6-109">Możesz użyć asemblera kontrolki na formularzu podobnym do innego formantu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f60b6-109">You can use the assembled control on a form like any other Windows Forms control.</span></span>

<span data-ttu-id="f60b6-110">Po zakończeniu pracy z tym przewodnikiem kontrolka niestandardowa będzie wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="f60b6-110">When you're finished with this walkthrough, your custom control will look something like the following:</span></span>

![Aplikacja wyświetlająca Neon z tekstem i przyciskami uruchamiania i zatrzymywania.](./media/creating-a-wf-control-design-time-features/demo-marquee-control.gif)

<span data-ttu-id="f60b6-112">Aby zapoznać się z pełną listą kodu, zobacz [How to: Create a Windows Forms Control, który korzysta z funkcji czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="f60b6-112">For the complete code listing, see [How to: Create a Windows Forms Control That Takes Advantage of Design-Time Features](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f60b6-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="f60b6-113">Prerequisites</span></span>

<span data-ttu-id="f60b6-114">Aby ukończyć ten przewodnik, musisz mieć program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f60b6-114">In order to complete this walkthrough, you'll need Visual Studio.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="f60b6-115">Utwórz projekt</span><span class="sxs-lookup"><span data-stu-id="f60b6-115">Create the project</span></span>

<span data-ttu-id="f60b6-116">Pierwszym krokiem jest utworzenie projektu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f60b6-116">The first step is to create the application project.</span></span> <span data-ttu-id="f60b6-117">Ten projekt będzie używany do kompilowania aplikacji, która hostuje kontrolkę niestandardową.</span><span class="sxs-lookup"><span data-stu-id="f60b6-117">You will use this project to build the application that hosts the custom control.</span></span>

<span data-ttu-id="f60b6-118">W programie Visual Studio Utwórz nowy projekt aplikacji Windows Forms, a następnie nadaj mu nazwę **MarqueeControlTest**.</span><span class="sxs-lookup"><span data-stu-id="f60b6-118">In Visual Studio, create a new Windows Forms Application project, and name it **MarqueeControlTest**.</span></span>

## <a name="create-the-control-library-project"></a><span data-ttu-id="f60b6-119">Tworzenie projektu biblioteki formantów</span><span class="sxs-lookup"><span data-stu-id="f60b6-119">Create the control library project</span></span>

1. <span data-ttu-id="f60b6-120">Dodaj projekt biblioteki formantów Windows Forms do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="f60b6-120">Add a Windows Forms Control Library project to the solution.</span></span> <span data-ttu-id="f60b6-121">Nazwij projekt **MarqueeControlLibrary**.</span><span class="sxs-lookup"><span data-stu-id="f60b6-121">Name the project **MarqueeControlLibrary**.</span></span>

2. <span data-ttu-id="f60b6-122">Korzystając z **Eksplorator rozwiązań**, usuń domyślną kontrolkę projektu, usuwając plik źródłowy o nazwie "UserControl1.cs" lub "UserControl1. vb", w zależności od wybranego języka.</span><span class="sxs-lookup"><span data-stu-id="f60b6-122">Using **Solution Explorer**, delete the project's default control by deleting the source file named "UserControl1.cs" or "UserControl1.vb", depending on your language of choice.</span></span>

3. <span data-ttu-id="f60b6-123">Dodaj nowy element <xref:System.Windows.Forms.UserControl> do projektu `MarqueeControlLibrary`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-123">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="f60b6-124">Nadaj nowemu plikowi źródłowej nazwę bazową **MarqueeControl**.</span><span class="sxs-lookup"><span data-stu-id="f60b6-124">Give the new source file a base name of **MarqueeControl**.</span></span>

4. <span data-ttu-id="f60b6-125">Korzystając z **Eksplorator rozwiązań**, Utwórz nowy folder w `MarqueeControlLibrary` projekcie.</span><span class="sxs-lookup"><span data-stu-id="f60b6-125">Using **Solution Explorer**, create a new folder in the `MarqueeControlLibrary` project.</span></span>

5. <span data-ttu-id="f60b6-126">Kliknij prawym przyciskiem myszy folder **projekt** i Dodaj nową klasę.</span><span class="sxs-lookup"><span data-stu-id="f60b6-126">Right-click the **Design** folder and add a new class.</span></span> <span data-ttu-id="f60b6-127">Nadaj mu nazwę **MarqueeControlRootDesigner**.</span><span class="sxs-lookup"><span data-stu-id="f60b6-127">Name it **MarqueeControlRootDesigner**.</span></span>

6. <span data-ttu-id="f60b6-128">Musisz użyć typów z zestawu System. Design, więc Dodaj to odwołanie do projektu `MarqueeControlLibrary`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-128">You'll need to use types from the System.Design assembly, so add this reference to the `MarqueeControlLibrary` project.</span></span>

## <a name="reference-the-custom-control-project"></a><span data-ttu-id="f60b6-129">Odwołuje się do projektu kontrolki niestandardowej</span><span class="sxs-lookup"><span data-stu-id="f60b6-129">Reference the Custom Control Project</span></span>

<span data-ttu-id="f60b6-130">Aby przetestować kontrolkę niestandardową, użyjesz projektu `MarqueeControlTest`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-130">You will use the `MarqueeControlTest` project to test the custom control.</span></span> <span data-ttu-id="f60b6-131">Projekt testowy zostanie powiadomiony o kontrolce niestandardowej po dodaniu odwołania do projektu do zestawu `MarqueeControlLibrary`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-131">The test project will become aware of the custom control when you add a project reference to the `MarqueeControlLibrary` assembly.</span></span>

<span data-ttu-id="f60b6-132">W projekcie `MarqueeControlTest` Dodaj odwołanie do projektu do zestawu `MarqueeControlLibrary`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-132">In the `MarqueeControlTest` project, add a project reference to the `MarqueeControlLibrary` assembly.</span></span> <span data-ttu-id="f60b6-133">Upewnij się, że korzystasz z karty **projekty** w oknie dialogowym **Dodaj odwołanie** zamiast odwoływać się bezpośrednio do zestawu `MarqueeControlLibrary`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-133">Be sure to use the **Projects** tab in the **Add Reference** dialog box instead of referencing the `MarqueeControlLibrary` assembly directly.</span></span>

## <a name="define-a-custom-control-and-its-custom-designer"></a><span data-ttu-id="f60b6-134">Zdefiniuj kontrolkę niestandardową i jej projektanta niestandardowego</span><span class="sxs-lookup"><span data-stu-id="f60b6-134">Define a Custom Control and Its Custom Designer</span></span>

<span data-ttu-id="f60b6-135">Kontrolka niestandardowa będzie pochodną klasy <xref:System.Windows.Forms.UserControl>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-135">Your custom control will derive from the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="f60b6-136">Dzięki temu formant może zawierać inne kontrolki i zapewnia kontrolę w dużej objęcie funkcją domyślną.</span><span class="sxs-lookup"><span data-stu-id="f60b6-136">This allows your control to contain other controls, and it gives your control a great deal of default functionality.</span></span>

<span data-ttu-id="f60b6-137">Kontrolka niestandardowa będzie dysponować skojarzonym projektantem niestandardowym.</span><span class="sxs-lookup"><span data-stu-id="f60b6-137">Your custom control will have an associated custom designer.</span></span> <span data-ttu-id="f60b6-138">Pozwala to na utworzenie unikatowego środowiska projektowego dopasowanego specjalnie do kontrolki niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="f60b6-138">This allows you to create a unique design experience tailored specifically for your custom control.</span></span>

<span data-ttu-id="f60b6-139">Formant można skojarzyć z jego projektantem za pomocą klasy <xref:System.ComponentModel.DesignerAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-139">You associate the control with its designer by using the <xref:System.ComponentModel.DesignerAttribute> class.</span></span> <span data-ttu-id="f60b6-140">Ponieważ opracowujesz całe zachowanie w czasie projektowania niestandardowej kontrolki, Projektant niestandardowy Zaimplementuj interfejs <xref:System.ComponentModel.Design.IRootDesigner>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-140">Because you are developing the entire design-time behavior of your custom control, the custom designer will implement the <xref:System.ComponentModel.Design.IRootDesigner> interface.</span></span>

### <a name="to-define-a-custom-control-and-its-custom-designer"></a><span data-ttu-id="f60b6-141">Aby zdefiniować kontrolkę niestandardową i jej projektanta niestandardowego</span><span class="sxs-lookup"><span data-stu-id="f60b6-141">To define a custom control and its custom designer</span></span>

1. <span data-ttu-id="f60b6-142">Otwórz plik źródłowy `MarqueeControl` w **edytorze kodu**.</span><span class="sxs-lookup"><span data-stu-id="f60b6-142">Open the `MarqueeControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="f60b6-143">W górnej części pliku Zaimportuj następujące przestrzenie nazw:</span><span class="sxs-lookup"><span data-stu-id="f60b6-143">At the top of the file, import the following namespaces:</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]

2. <span data-ttu-id="f60b6-144">Dodaj <xref:System.ComponentModel.DesignerAttribute> do deklaracji klasy `MarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-144">Add the <xref:System.ComponentModel.DesignerAttribute> to the `MarqueeControl` class declaration.</span></span> <span data-ttu-id="f60b6-145">Powoduje to skojarzenie kontrolki niestandardowej z jej projektantem.</span><span class="sxs-lookup"><span data-stu-id="f60b6-145">This associates the custom control with its designer.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]

3. <span data-ttu-id="f60b6-146">Otwórz plik źródłowy `MarqueeControlRootDesigner` w **edytorze kodu**.</span><span class="sxs-lookup"><span data-stu-id="f60b6-146">Open the `MarqueeControlRootDesigner` source file in the **Code Editor**.</span></span> <span data-ttu-id="f60b6-147">W górnej części pliku Zaimportuj następujące przestrzenie nazw:</span><span class="sxs-lookup"><span data-stu-id="f60b6-147">At the top of the file, import the following namespaces:</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]

4. <span data-ttu-id="f60b6-148">Zmień deklarację `MarqueeControlRootDesigner` na dziedziczenie z klasy <xref:System.Windows.Forms.Design.DocumentDesigner>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-148">Change the declaration of `MarqueeControlRootDesigner` to inherit from the <xref:System.Windows.Forms.Design.DocumentDesigner> class.</span></span> <span data-ttu-id="f60b6-149">Zastosuj <xref:System.ComponentModel.ToolboxItemFilterAttribute>, aby określić interakcję projektanta z **przybornikiem**.</span><span class="sxs-lookup"><span data-stu-id="f60b6-149">Apply the <xref:System.ComponentModel.ToolboxItemFilterAttribute> to specify the designer interaction with the **Toolbox**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="f60b6-150">Definicja klasy `MarqueeControlRootDesigner` została ujęta w przestrzeń nazw o nazwie MarqueeControlLibrary. Design.</span><span class="sxs-lookup"><span data-stu-id="f60b6-150">The definition for the `MarqueeControlRootDesigner` class has been enclosed in a namespace called MarqueeControlLibrary.Design.</span></span> <span data-ttu-id="f60b6-151">Ta deklaracja umieszcza projektanta w specjalnej przestrzeni nazw zarezerwowanej dla typów związanych z projektem.</span><span class="sxs-lookup"><span data-stu-id="f60b6-151">This declaration places the designer in a special namespace reserved for design-related types.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]

5. <span data-ttu-id="f60b6-152">Zdefiniuj konstruktora dla klasy `MarqueeControlRootDesigner`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-152">Define the constructor for the `MarqueeControlRootDesigner` class.</span></span> <span data-ttu-id="f60b6-153">Wstaw instrukcję <xref:System.Diagnostics.Trace.WriteLine%2A> w treści konstruktora.</span><span class="sxs-lookup"><span data-stu-id="f60b6-153">Insert a <xref:System.Diagnostics.Trace.WriteLine%2A> statement in the constructor body.</span></span> <span data-ttu-id="f60b6-154">Będzie to przydatne podczas debugowania.</span><span class="sxs-lookup"><span data-stu-id="f60b6-154">This will be useful for debugging.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]

## <a name="create-an-instance-of-your-custom-control"></a><span data-ttu-id="f60b6-155">Tworzenie wystąpienia kontrolki niestandardowej</span><span class="sxs-lookup"><span data-stu-id="f60b6-155">Create an instance of your custom control</span></span>

1. <span data-ttu-id="f60b6-156">Dodaj nowy element <xref:System.Windows.Forms.UserControl> do projektu `MarqueeControlTest`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-156">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlTest` project.</span></span> <span data-ttu-id="f60b6-157">Nadaj nowemu plikowi źródłowej nazwę bazową **DemoMarqueeControl**.</span><span class="sxs-lookup"><span data-stu-id="f60b6-157">Give the new source file a base name of **DemoMarqueeControl**.</span></span>

2. <span data-ttu-id="f60b6-158">Otwórz plik `DemoMarqueeControl` w **edytorze kodu**.</span><span class="sxs-lookup"><span data-stu-id="f60b6-158">Open the `DemoMarqueeControl` file in the **Code Editor**.</span></span> <span data-ttu-id="f60b6-159">W górnej części pliku zaimportuj `MarqueeControlLibrary` przestrzeń nazw:</span><span class="sxs-lookup"><span data-stu-id="f60b6-159">At the top of the file, import the `MarqueeControlLibrary` namespace:</span></span>

   ```vb
   Imports MarqueeControlLibrary
   ```

   ```csharp
   using MarqueeControlLibrary;
   ```

3. <span data-ttu-id="f60b6-160">Zmień deklarację `DemoMarqueeControl` na dziedziczenie z klasy `MarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-160">Change the declaration of `DemoMarqueeControl` to inherit from the `MarqueeControl` class.</span></span>

4. <span data-ttu-id="f60b6-161">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="f60b6-161">Build the project.</span></span>

5. <span data-ttu-id="f60b6-162">Otwórz formularz Form1 w Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="f60b6-162">Open Form1 in the Windows Forms Designer.</span></span>

6. <span data-ttu-id="f60b6-163">Znajdź kartę **składniki MarqueeControlTest** w **przyborniku** i otwórz ją.</span><span class="sxs-lookup"><span data-stu-id="f60b6-163">Find the **MarqueeControlTest Components** tab in the **Toolbox** and open it.</span></span> <span data-ttu-id="f60b6-164">Przeciągnij `DemoMarqueeControl` z **przybornika** do formularza.</span><span class="sxs-lookup"><span data-stu-id="f60b6-164">Drag a `DemoMarqueeControl` from the **Toolbox** onto your form.</span></span>

7. <span data-ttu-id="f60b6-165">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="f60b6-165">Build the project.</span></span>

## <a name="set-up-the-project-for-design-time-debugging"></a><span data-ttu-id="f60b6-166">Konfigurowanie projektu na potrzeby debugowania w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="f60b6-166">Set Up the Project for Design-Time Debugging</span></span>

<span data-ttu-id="f60b6-167">Podczas opracowywania niestandardowego środowiska czasu projektowania konieczne będzie Debugowanie formantów i składników.</span><span class="sxs-lookup"><span data-stu-id="f60b6-167">When you're developing a custom design-time experience, it will be necessary to debug your controls and components.</span></span> <span data-ttu-id="f60b6-168">Istnieje prosty sposób skonfigurowania projektu w taki sposób, aby zezwalał na Debugowanie w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="f60b6-168">There is a simple way to set up your project to allow debugging at design time.</span></span> <span data-ttu-id="f60b6-169">Aby uzyskać więcej informacji, zobacz [Przewodnik: debugowanie niestandardowych kontrolek Windows Forms w czasie projektowania](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="f60b6-169">For more information, see [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>

1. <span data-ttu-id="f60b6-170">Kliknij prawym przyciskiem myszy projekt `MarqueeControlLibrary` i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="f60b6-170">Right-click the `MarqueeControlLibrary` project and select **Properties**.</span></span>

2. <span data-ttu-id="f60b6-171">W oknie dialogowym **MarqueeControlLibrary strony właściwości** wybierz stronę **debugowanie** .</span><span class="sxs-lookup"><span data-stu-id="f60b6-171">In the **MarqueeControlLibrary Property Pages** dialog box, select the **Debug** page.</span></span>

3. <span data-ttu-id="f60b6-172">W sekcji **Akcja początkowa** wybierz pozycję **Uruchom program zewnętrzny**.</span><span class="sxs-lookup"><span data-stu-id="f60b6-172">In the **Start Action** section, select **Start External Program**.</span></span> <span data-ttu-id="f60b6-173">Będziesz debugować osobne wystąpienie programu Visual Studio, więc kliknij przycisk wielokropka (![przycisk wielokropka (...) na okno Właściwości przycisku programu Visual Studio](./media/visual-studio-ellipsis-button.png)), aby wyszukać środowisko IDE programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f60b6-173">You will be debugging a separate instance of Visual Studio, so click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) button to browse for the Visual Studio IDE.</span></span> <span data-ttu-id="f60b6-174">Nazwa pliku wykonywalnego to devenv. exe, a jeśli została zainstalowana w lokalizacji domyślnej, jego ścieżka to *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\\\<edition > \Common7\IDE\devenv.exe*.</span><span class="sxs-lookup"><span data-stu-id="f60b6-174">The name of the executable file is devenv.exe, and if you installed to the default location, its path is *%ProgramFiles(x86)%\Microsoft Visual Studio\2019\\\<edition>\Common7\IDE\devenv.exe*.</span></span>

4. <span data-ttu-id="f60b6-175">Wybierz przycisk **OK**, aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="f60b6-175">Select **OK** to close the dialog box.</span></span>

5. <span data-ttu-id="f60b6-176">Kliknij prawym przyciskiem myszy projekt MarqueeControlLibrary i wybierz pozycję **Ustaw jako projekt startowy** , aby włączyć tę konfigurację debugowania.</span><span class="sxs-lookup"><span data-stu-id="f60b6-176">Right-click the MarqueeControlLibrary project and select **Set as StartUp Project** to enable this debugging configuration.</span></span>

## <a name="checkpoint"></a><span data-ttu-id="f60b6-177">Punkt kontrolny</span><span class="sxs-lookup"><span data-stu-id="f60b6-177">Checkpoint</span></span>

<span data-ttu-id="f60b6-178">Teraz można przystąpić do debugowania zachowania niestandardowej kontrolki czasu projektowania.</span><span class="sxs-lookup"><span data-stu-id="f60b6-178">You are now ready to debug the design-time behavior of your custom control.</span></span> <span data-ttu-id="f60b6-179">Po ustaleniu, że środowisko debugowania jest prawidłowo skonfigurowane, należy przetestować skojarzenie między kontrolką niestandardową a projektantem niestandardowym.</span><span class="sxs-lookup"><span data-stu-id="f60b6-179">Once you've determined that the debugging environment is set up correctly, you'll test the association between the custom control and the custom designer.</span></span>

### <a name="to-test-the-debugging-environment-and-the-designer-association"></a><span data-ttu-id="f60b6-180">Aby przetestować środowisko debugowania i skojarzenie projektanta</span><span class="sxs-lookup"><span data-stu-id="f60b6-180">To test the debugging environment and the designer association</span></span>

1. <span data-ttu-id="f60b6-181">Otwórz plik źródłowy MarqueeControlRootDesigner w **edytorze kodu** i umieść punkt przerwania w instrukcji <xref:System.Diagnostics.Trace.WriteLine%2A>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-181">Open the MarqueeControlRootDesigner source file in the **Code Editor** and place a breakpoint on the <xref:System.Diagnostics.Trace.WriteLine%2A> statement.</span></span>

2. <span data-ttu-id="f60b6-182">Naciśnij klawisz **F5** , aby rozpocząć sesję debugowania.</span><span class="sxs-lookup"><span data-stu-id="f60b6-182">Press **F5** to start the debugging session.</span></span>

   <span data-ttu-id="f60b6-183">Zostanie utworzone nowe wystąpienie programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f60b6-183">A new instance of Visual Studio is created.</span></span>

3. <span data-ttu-id="f60b6-184">W nowym wystąpieniu programu Visual Studio Otwórz rozwiązanie MarqueeControlTest.</span><span class="sxs-lookup"><span data-stu-id="f60b6-184">In the new instance of Visual Studio, open the MarqueeControlTest solution.</span></span> <span data-ttu-id="f60b6-185">Możesz łatwo znaleźć rozwiązanie, wybierając pozycję **ostatnie projekty** z menu **plik** .</span><span class="sxs-lookup"><span data-stu-id="f60b6-185">You can easily find the solution by selecting **Recent Projects** from the **File** menu.</span></span> <span data-ttu-id="f60b6-186">Plik rozwiązania MarqueeControlTest. sln zostanie wyświetlony jako ostatnio używany plik.</span><span class="sxs-lookup"><span data-stu-id="f60b6-186">The MarqueeControlTest.sln solution file will be listed as the most recently used file.</span></span>

4. <span data-ttu-id="f60b6-187">Otwórz `DemoMarqueeControl` w projektancie.</span><span class="sxs-lookup"><span data-stu-id="f60b6-187">Open the `DemoMarqueeControl` in the designer.</span></span>

   <span data-ttu-id="f60b6-188">Wystąpienie debugowania programu Visual Studio uzyskuje fokus i wykonywanie jest zatrzymywane w punkcie przerwania.</span><span class="sxs-lookup"><span data-stu-id="f60b6-188">The debugging instance of Visual Studio obtains focus and execution stops at your breakpoint.</span></span> <span data-ttu-id="f60b6-189">Naciśnij klawisz **F5** , aby kontynuować sesję debugowania.</span><span class="sxs-lookup"><span data-stu-id="f60b6-189">Press **F5** to continue the debugging session.</span></span>

<span data-ttu-id="f60b6-190">W tym momencie wszystko jest używane do tworzenia i debugowania formantu niestandardowego oraz skojarzonego z nim projektanta niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="f60b6-190">At this point, everything is in place for you to develop and debug your custom control and its associated custom designer.</span></span> <span data-ttu-id="f60b6-191">Pozostała część tego artykułu koncentruje się na szczegółach implementacji funkcji formantu i projektanta.</span><span class="sxs-lookup"><span data-stu-id="f60b6-191">The remainder of this article concentrates on the details of implementing features of the control and the designer.</span></span>

## <a name="implement-the-custom-control"></a><span data-ttu-id="f60b6-192">Implementowanie kontrolki niestandardowej</span><span class="sxs-lookup"><span data-stu-id="f60b6-192">Implement the Custom Control</span></span>

<span data-ttu-id="f60b6-193">`MarqueeControl` to <xref:System.Windows.Forms.UserControl> z małą ilością dostosowywać.</span><span class="sxs-lookup"><span data-stu-id="f60b6-193">The `MarqueeControl` is a <xref:System.Windows.Forms.UserControl> with a little bit of customization.</span></span> <span data-ttu-id="f60b6-194">Przedstawia dwie metody: `Start`, która uruchamia animację neonu i `Stop`, która powoduje zatrzymanie animacji.</span><span class="sxs-lookup"><span data-stu-id="f60b6-194">It exposes two methods: `Start`, which starts the marquee animation, and `Stop`, which stops the animation.</span></span> <span data-ttu-id="f60b6-195">Ponieważ `MarqueeControl` zawiera kontrolki podrzędne implementujące interfejs `IMarqueeWidget`, `Start` i `Stop` wyliczają poszczególne kontrolki podrzędne i wywołują odpowiednio metody `StartMarquee` i `StopMarquee`, na każdym formancie podrzędnym, który implementuje `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-195">Because the `MarqueeControl` contains child controls that implement the `IMarqueeWidget` interface, `Start` and `Stop` enumerate each child control and call the `StartMarquee` and `StopMarquee` methods, respectively, on each child control that implements `IMarqueeWidget`.</span></span>

<span data-ttu-id="f60b6-196">Wygląd `MarqueeBorder` i kontrolek `MarqueeText` zależy od układu, dlatego `MarqueeControl` przesłania metodę <xref:System.Windows.Forms.Control.OnLayout%2A> i wywołuje <xref:System.Windows.Forms.Control.PerformLayout%2A> w kontrolkach podrzędnych tego typu.</span><span class="sxs-lookup"><span data-stu-id="f60b6-196">The appearance of the `MarqueeBorder` and `MarqueeText` controls is dependent on the layout, so `MarqueeControl` overrides the <xref:System.Windows.Forms.Control.OnLayout%2A> method and calls <xref:System.Windows.Forms.Control.PerformLayout%2A> on child controls of this type.</span></span>

<span data-ttu-id="f60b6-197">Jest to zakres dostosowań `MarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-197">This is the extent of the `MarqueeControl` customizations.</span></span> <span data-ttu-id="f60b6-198">Funkcje czasu wykonywania są implementowane przez `MarqueeBorder` i `MarqueeText` kontrolki, a funkcje czasu projektowania są implementowane przez klasy `MarqueeBorderDesigner` i `MarqueeControlRootDesigner`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-198">The run-time features are implemented by the `MarqueeBorder` and `MarqueeText` controls, and the design-time features are implemented by the `MarqueeBorderDesigner` and `MarqueeControlRootDesigner` classes.</span></span>

### <a name="to-implement-your-custom-control"></a><span data-ttu-id="f60b6-199">Aby zaimplementować kontrolkę niestandardową</span><span class="sxs-lookup"><span data-stu-id="f60b6-199">To implement your custom control</span></span>

1. <span data-ttu-id="f60b6-200">Otwórz plik źródłowy `MarqueeControl` w **edytorze kodu**.</span><span class="sxs-lookup"><span data-stu-id="f60b6-200">Open the `MarqueeControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="f60b6-201">Zaimplementuj metody `Start` i `Stop`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-201">Implement the `Start` and `Stop` methods.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]

2. <span data-ttu-id="f60b6-202">Zastąp metodę <xref:System.Windows.Forms.Control.OnLayout%2A>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-202">Override the <xref:System.Windows.Forms.Control.OnLayout%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]

## <a name="create-a-child-control-for-your-custom-control"></a><span data-ttu-id="f60b6-203">Utwórz kontrolkę podrzędną dla kontrolki niestandardowej</span><span class="sxs-lookup"><span data-stu-id="f60b6-203">Create a Child Control for Your Custom Control</span></span>

<span data-ttu-id="f60b6-204">`MarqueeControl` będzie hostować dwa rodzaje kontrolki podrzędnej: formant `MarqueeBorder` i kontrolka `MarqueeText`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-204">The `MarqueeControl` will host two kinds of child control: the `MarqueeBorder` control and the `MarqueeText` control.</span></span>

- <span data-ttu-id="f60b6-205">`MarqueeBorder`: ten formant maluje obramowanie "świateł" wokół jego krawędzi.</span><span class="sxs-lookup"><span data-stu-id="f60b6-205">`MarqueeBorder`: This control paints a border of "lights" around its edges.</span></span> <span data-ttu-id="f60b6-206">Lampki są błyskowe, aby były widoczne wokół krawędzi.</span><span class="sxs-lookup"><span data-stu-id="f60b6-206">The lights flash in sequence, so they appear to be moving around the border.</span></span> <span data-ttu-id="f60b6-207">Szybkość, z jaką lampy błyskowe są kontrolowane przez właściwość o nazwie `UpdatePeriod`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-207">The speed at which the lights flash is controlled by a property called `UpdatePeriod`.</span></span> <span data-ttu-id="f60b6-208">Kilka innych właściwości niestandardowych określa inne aspekty wyglądu kontrolki.</span><span class="sxs-lookup"><span data-stu-id="f60b6-208">Several other custom properties determine other aspects of the control's appearance.</span></span> <span data-ttu-id="f60b6-209">Dwie metody, nazywane `StartMarquee` i `StopMarquee`, kontrolują, kiedy animacja zaczyna się i zatrzyma.</span><span class="sxs-lookup"><span data-stu-id="f60b6-209">Two methods, called `StartMarquee` and `StopMarquee`, control when the animation starts and stops.</span></span>

- <span data-ttu-id="f60b6-210">`MarqueeText`: ten formant maluje migający ciąg.</span><span class="sxs-lookup"><span data-stu-id="f60b6-210">`MarqueeText`: This control paints a flashing string.</span></span> <span data-ttu-id="f60b6-211">Podobnie jak w przypadku kontrolki `MarqueeBorder`, szybkość, z jaką błysk tekstu jest kontrolowana przez właściwość `UpdatePeriod`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-211">Like the `MarqueeBorder` control, the speed at which the text flashes is controlled by the `UpdatePeriod` property.</span></span> <span data-ttu-id="f60b6-212">Kontrolka `MarqueeText` ma także metody `StartMarquee` i `StopMarquee` wspólne z formantem `MarqueeBorder`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-212">The `MarqueeText` control also has the `StartMarquee` and `StopMarquee` methods in common with the `MarqueeBorder` control.</span></span>

<span data-ttu-id="f60b6-213">W czasie projektowania `MarqueeControlRootDesigner` zezwala na dodawanie tych dwóch typów formantów do `MarqueeControl` w dowolnej kombinacji.</span><span class="sxs-lookup"><span data-stu-id="f60b6-213">At design time, the `MarqueeControlRootDesigner` allows these two control types to be added to a `MarqueeControl` in any combination.</span></span>

<span data-ttu-id="f60b6-214">Typowe funkcje obu formantów są uwzględniane w interfejsie o nazwie `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-214">Common features of the two controls are factored into an interface called `IMarqueeWidget`.</span></span> <span data-ttu-id="f60b6-215">Dzięki temu `MarqueeControl` odnajdywania dowolnych kontrolek podrzędnych związanych z neonem i nadawać im specjalne traktowanie.</span><span class="sxs-lookup"><span data-stu-id="f60b6-215">This allows the `MarqueeControl` to discover any Marquee-related child controls and give them special treatment.</span></span>

<span data-ttu-id="f60b6-216">Aby zaimplementować funkcję okresowej animacji, użyjesz <xref:System.ComponentModel.BackgroundWorker> obiektów z przestrzeni nazw <xref:System.ComponentModel?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-216">To implement the periodic animation feature, you will use <xref:System.ComponentModel.BackgroundWorker> objects from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="f60b6-217">Można użyć <xref:System.Windows.Forms.Timer> obiektów, ale jeśli istnieją wiele obiektów `IMarqueeWidget`, wątek pojedynczego interfejsu użytkownika może nie być w stanie zachować animacji.</span><span class="sxs-lookup"><span data-stu-id="f60b6-217">You could use <xref:System.Windows.Forms.Timer> objects, but when many `IMarqueeWidget` objects are present, the single UI thread may be unable to keep up with the animation.</span></span>

### <a name="to-create-a-child-control-for-your-custom-control"></a><span data-ttu-id="f60b6-218">Aby utworzyć kontrolkę podrzędną dla kontrolki niestandardowej</span><span class="sxs-lookup"><span data-stu-id="f60b6-218">To create a child control for your custom control</span></span>

1. <span data-ttu-id="f60b6-219">Dodaj nowy element klasy do projektu `MarqueeControlLibrary`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-219">Add a new class item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="f60b6-220">Nadaj nowemu plikowi źródłowej nazwę podstawową "IMarqueeWidget".</span><span class="sxs-lookup"><span data-stu-id="f60b6-220">Give the new source file a base name of "IMarqueeWidget."</span></span>

2. <span data-ttu-id="f60b6-221">Otwórz plik źródłowy `IMarqueeWidget` w **edytorze kodu** i zmień deklarację z `class` na `interface`:</span><span class="sxs-lookup"><span data-stu-id="f60b6-221">Open the `IMarqueeWidget` source file in the **Code Editor** and change the declaration from `class` to `interface`:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]

3. <span data-ttu-id="f60b6-222">Dodaj następujący kod do interfejsu `IMarqueeWidget`, aby uwidocznić dwie metody i właściwość, która manipuluje animacją neonu:</span><span class="sxs-lookup"><span data-stu-id="f60b6-222">Add the following code to the `IMarqueeWidget` interface to expose two methods and a property that manipulate the marquee animation:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]

4. <span data-ttu-id="f60b6-223">Dodaj nowy element **kontrolki niestandardowej** do projektu `MarqueeControlLibrary`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-223">Add a new **Custom Control** item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="f60b6-224">Nadaj nowemu plikowi źródłowej nazwę podstawową "MarqueeText".</span><span class="sxs-lookup"><span data-stu-id="f60b6-224">Give the new source file a base name of "MarqueeText."</span></span>

5. <span data-ttu-id="f60b6-225">Przeciągnij składnik <xref:System.ComponentModel.BackgroundWorker> z **przybornika** na kontrolkę `MarqueeText`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-225">Drag a <xref:System.ComponentModel.BackgroundWorker> component from the **Toolbox** onto your `MarqueeText` control.</span></span> <span data-ttu-id="f60b6-226">Ten składnik zezwoli formantowi `MarqueeText` do samodzielnego aktualizowania.</span><span class="sxs-lookup"><span data-stu-id="f60b6-226">This component will allow the `MarqueeText` control to update itself asynchronously.</span></span>

6. <span data-ttu-id="f60b6-227">W oknie **Właściwości** ustaw właściwości `WorkerReportsProgress` i <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> składnika <xref:System.ComponentModel.BackgroundWorker> na **wartość true**.</span><span class="sxs-lookup"><span data-stu-id="f60b6-227">In the **Properties** window, set the <xref:System.ComponentModel.BackgroundWorker> component's `WorkerReportsProgress` and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to **true**.</span></span> <span data-ttu-id="f60b6-228">Te ustawienia umożliwiają składnikowi <xref:System.ComponentModel.BackgroundWorker> okresowe zgłaszanie zdarzenia <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> i anulowanie aktualizacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="f60b6-228">These settings allow the <xref:System.ComponentModel.BackgroundWorker> component to periodically raise the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event and to cancel asynchronous updates.</span></span>

   <span data-ttu-id="f60b6-229">Aby uzyskać więcej informacji, zobacz [składnik BackgroundWorker](backgroundworker-component.md).</span><span class="sxs-lookup"><span data-stu-id="f60b6-229">For more information, see [BackgroundWorker Component](backgroundworker-component.md).</span></span>

7. <span data-ttu-id="f60b6-230">Otwórz plik źródłowy `MarqueeText` w **edytorze kodu**.</span><span class="sxs-lookup"><span data-stu-id="f60b6-230">Open the `MarqueeText` source file in the **Code Editor**.</span></span> <span data-ttu-id="f60b6-231">W górnej części pliku Zaimportuj następujące przestrzenie nazw:</span><span class="sxs-lookup"><span data-stu-id="f60b6-231">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]

8. <span data-ttu-id="f60b6-232">Zmień deklarację `MarqueeText`, aby dziedziczyć po <xref:System.Windows.Forms.Label> i zaimplementować interfejs `IMarqueeWidget`:</span><span class="sxs-lookup"><span data-stu-id="f60b6-232">Change the declaration of `MarqueeText` to inherit from <xref:System.Windows.Forms.Label> and to implement the `IMarqueeWidget` interface:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]

9. <span data-ttu-id="f60b6-233">Zadeklaruj zmienne wystąpienia, które odpowiadają uwidocznionym właściwościom, i zainicjuj je w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="f60b6-233">Declare the instance variables that correspond to the exposed properties, and initialize them in the constructor.</span></span> <span data-ttu-id="f60b6-234">Pole `isLit` określa, czy tekst ma być malowany w kolorze podanym przez właściwość `LightColor`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-234">The `isLit` field determines if the text is to be painted in the color given by the `LightColor` property.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]

10. <span data-ttu-id="f60b6-235">Zaimplementuj interfejs `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-235">Implement the `IMarqueeWidget` interface.</span></span>

    <span data-ttu-id="f60b6-236">Metody `StartMarquee` i `StopMarquee` wywołują metody <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> i <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> składnika <xref:System.ComponentModel.BackgroundWorker>, aby uruchomić i zatrzymać animację.</span><span class="sxs-lookup"><span data-stu-id="f60b6-236">The `StartMarquee` and `StopMarquee` methods invoke the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> methods to start and stop the animation.</span></span>

    <span data-ttu-id="f60b6-237">Atrybuty <xref:System.ComponentModel.CategoryAttribute.Category%2A> i <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> są stosowane do właściwości `UpdatePeriod`, dlatego pojawiają się w sekcji niestandardowej okno Właściwości o nazwie "Markiza".</span><span class="sxs-lookup"><span data-stu-id="f60b6-237">The <xref:System.ComponentModel.CategoryAttribute.Category%2A> and <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> attributes are applied to the `UpdatePeriod` property so it appears in a custom section of the Properties window called "Marquee."</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]

11. <span data-ttu-id="f60b6-238">Zaimplementuj metody dostępu do właściwości.</span><span class="sxs-lookup"><span data-stu-id="f60b6-238">Implement the property accessors.</span></span> <span data-ttu-id="f60b6-239">Udostępnimy dwie właściwości klientom: `LightColor` i `DarkColor`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-239">You'll expose two properties to clients: `LightColor` and `DarkColor`.</span></span> <span data-ttu-id="f60b6-240">Atrybuty <xref:System.ComponentModel.CategoryAttribute.Category%2A> i <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> są stosowane do tych właściwości, więc właściwości są wyświetlane w sekcji niestandardowej okno Właściwości o nazwie "neon".</span><span class="sxs-lookup"><span data-stu-id="f60b6-240">The <xref:System.ComponentModel.CategoryAttribute.Category%2A> and <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> attributes are applied to these properties, so the properties appear in a custom section of the Properties window called "Marquee."</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]

12. <span data-ttu-id="f60b6-241">Zaimplementuj programy obsługi dla zdarzeń <xref:System.ComponentModel.BackgroundWorker.DoWork> i <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> składnika <xref:System.ComponentModel.BackgroundWorker>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-241">Implement the handlers for the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

    <span data-ttu-id="f60b6-242">Procedura obsługi zdarzeń <xref:System.ComponentModel.BackgroundWorker.DoWork> uśpienia dla liczby milisekund określonych przez `UpdatePeriod` następnie wywołuje zdarzenie <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>, dopóki kod nie zatrzyma animacji przez wywołanie <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-242">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler sleeps for the number of milliseconds specified by `UpdatePeriod` then raises the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, until your code stops the animation by calling <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span></span>

    <span data-ttu-id="f60b6-243">Obsługa zdarzeń <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> przełącza tekst między jego oświetleniem i ciemnym stanem w celu uzyskania migania.</span><span class="sxs-lookup"><span data-stu-id="f60b6-243">The <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler toggles the text between its light and dark state to give the appearance of flashing.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]

13. <span data-ttu-id="f60b6-244">Zastąp metodę <xref:System.Windows.Forms.Control.OnPaint%2A>, aby włączyć animację.</span><span class="sxs-lookup"><span data-stu-id="f60b6-244">Override the <xref:System.Windows.Forms.Control.OnPaint%2A> method to enable the animation.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]

14. <span data-ttu-id="f60b6-245">Naciśnij klawisz **F6** , aby skompilować rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="f60b6-245">Press **F6** to build the solution.</span></span>

## <a name="create-the-marqueeborder-child-control"></a><span data-ttu-id="f60b6-246">Utwórz formant podrzędny MarqueeBorder</span><span class="sxs-lookup"><span data-stu-id="f60b6-246">Create the MarqueeBorder Child Control</span></span>

<span data-ttu-id="f60b6-247">Formant `MarqueeBorder` jest nieco bardziej skomplikowany niż kontrolka `MarqueeText`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-247">The `MarqueeBorder` control is slightly more sophisticated than the `MarqueeText` control.</span></span> <span data-ttu-id="f60b6-248">Ma więcej właściwości, a animacja w metodzie <xref:System.Windows.Forms.Control.OnPaint%2A> jest większa.</span><span class="sxs-lookup"><span data-stu-id="f60b6-248">It has more properties and the animation in the <xref:System.Windows.Forms.Control.OnPaint%2A> method is more involved.</span></span> <span data-ttu-id="f60b6-249">Zasadniczo jest to bardzo podobne do kontrolki `MarqueeText`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-249">In principle, it is quite similar to the `MarqueeText` control.</span></span>

<span data-ttu-id="f60b6-250">Ponieważ kontrolka `MarqueeBorder` może mieć kontrolki podrzędne, musi mieć świadomość zdarzeń <xref:System.Windows.Forms.Control.Layout>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-250">Because the `MarqueeBorder` control can have child controls, it needs to be aware of <xref:System.Windows.Forms.Control.Layout> events.</span></span>

### <a name="to-create-the-marqueeborder-control"></a><span data-ttu-id="f60b6-251">Aby utworzyć formant MarqueeBorder</span><span class="sxs-lookup"><span data-stu-id="f60b6-251">To create the MarqueeBorder control</span></span>

1. <span data-ttu-id="f60b6-252">Dodaj nowy element **kontrolki niestandardowej** do projektu `MarqueeControlLibrary`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-252">Add a new **Custom Control** item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="f60b6-253">Nadaj nowemu plikowi źródłowej nazwę podstawową "MarqueeBorder".</span><span class="sxs-lookup"><span data-stu-id="f60b6-253">Give the new source file a base name of "MarqueeBorder."</span></span>

2. <span data-ttu-id="f60b6-254">Przeciągnij składnik <xref:System.ComponentModel.BackgroundWorker> z **przybornika** na kontrolkę `MarqueeBorder`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-254">Drag a <xref:System.ComponentModel.BackgroundWorker> component from the **Toolbox** onto your `MarqueeBorder` control.</span></span> <span data-ttu-id="f60b6-255">Ten składnik zezwoli formantowi `MarqueeBorder` do samodzielnego aktualizowania.</span><span class="sxs-lookup"><span data-stu-id="f60b6-255">This component will allow the `MarqueeBorder` control to update itself asynchronously.</span></span>

3. <span data-ttu-id="f60b6-256">W oknie **Właściwości** ustaw właściwości `WorkerReportsProgress` i <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> składnika <xref:System.ComponentModel.BackgroundWorker> na **wartość true**.</span><span class="sxs-lookup"><span data-stu-id="f60b6-256">In the **Properties** window, set the <xref:System.ComponentModel.BackgroundWorker> component's `WorkerReportsProgress` and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to **true**.</span></span> <span data-ttu-id="f60b6-257">Te ustawienia umożliwiają składnikowi <xref:System.ComponentModel.BackgroundWorker> okresowe zgłaszanie zdarzenia <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> i anulowanie aktualizacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="f60b6-257">These settings allow the <xref:System.ComponentModel.BackgroundWorker> component to periodically raise the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event and to cancel asynchronous updates.</span></span> <span data-ttu-id="f60b6-258">Aby uzyskać więcej informacji, zobacz [składnik BackgroundWorker](backgroundworker-component.md).</span><span class="sxs-lookup"><span data-stu-id="f60b6-258">For more information, see [BackgroundWorker Component](backgroundworker-component.md).</span></span>

4. <span data-ttu-id="f60b6-259">W oknie **Właściwości** wybierz przycisk **zdarzenia** .</span><span class="sxs-lookup"><span data-stu-id="f60b6-259">In the **Properties** window, select the **Events** button.</span></span> <span data-ttu-id="f60b6-260">Dołącz programy obsługi dla zdarzeń <xref:System.ComponentModel.BackgroundWorker.DoWork> i <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-260">Attach handlers for the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

5. <span data-ttu-id="f60b6-261">Otwórz plik źródłowy `MarqueeBorder` w **edytorze kodu**.</span><span class="sxs-lookup"><span data-stu-id="f60b6-261">Open the `MarqueeBorder` source file in the **Code Editor**.</span></span> <span data-ttu-id="f60b6-262">W górnej części pliku Zaimportuj następujące przestrzenie nazw:</span><span class="sxs-lookup"><span data-stu-id="f60b6-262">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]

6. <span data-ttu-id="f60b6-263">Zmień deklarację `MarqueeBorder`, aby dziedziczyć po <xref:System.Windows.Forms.Panel> i zaimplementować interfejs `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-263">Change the declaration of `MarqueeBorder` to inherit from <xref:System.Windows.Forms.Panel> and to implement the `IMarqueeWidget` interface.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]

7. <span data-ttu-id="f60b6-264">Zadeklaruj dwa wyliczenia, aby zarządzać stanem kontrolki `MarqueeBorder`: `MarqueeSpinDirection`, która określa kierunek, w którym sygnalizatory "pokrętło" wokół obramowania i `MarqueeLightShape`, które określają kształt świateł (kwadrat lub okrągły).</span><span class="sxs-lookup"><span data-stu-id="f60b6-264">Declare two enumerations for managing the `MarqueeBorder` control's state: `MarqueeSpinDirection`, which determines the direction in which the lights "spin" around the border, and `MarqueeLightShape`, which determines the shape of the lights (square or circular).</span></span> <span data-ttu-id="f60b6-265">Należy umieścić te deklaracje przed deklaracją klasy `MarqueeBorder`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-265">Place these declarations before the `MarqueeBorder` class declaration.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]

8. <span data-ttu-id="f60b6-266">Zadeklaruj zmienne wystąpienia, które odpowiadają uwidocznionym właściwościom, i zainicjuj je w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="f60b6-266">Declare the instance variables that correspond to the exposed properties, and initialize them in the constructor.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]

9. <span data-ttu-id="f60b6-267">Zaimplementuj interfejs `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-267">Implement the `IMarqueeWidget` interface.</span></span>

    <span data-ttu-id="f60b6-268">Metody `StartMarquee` i `StopMarquee` wywołują metody <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> i <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> składnika <xref:System.ComponentModel.BackgroundWorker>, aby uruchomić i zatrzymać animację.</span><span class="sxs-lookup"><span data-stu-id="f60b6-268">The `StartMarquee` and `StopMarquee` methods invoke the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> methods to start and stop the animation.</span></span>

    <span data-ttu-id="f60b6-269">Ponieważ kontrolka `MarqueeBorder` może zawierać kontrolki podrzędne, Metoda `StartMarquee` wylicza wszystkie kontrolki podrzędne i wywołuje `StartMarquee` na tych, które implementują `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-269">Because the `MarqueeBorder` control can contain child controls, the `StartMarquee` method enumerates all child controls and calls `StartMarquee` on those that implement `IMarqueeWidget`.</span></span> <span data-ttu-id="f60b6-270">Metoda `StopMarquee` ma podobną implementację.</span><span class="sxs-lookup"><span data-stu-id="f60b6-270">The `StopMarquee` method has a similar implementation.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]

10. <span data-ttu-id="f60b6-271">Zaimplementuj metody dostępu do właściwości.</span><span class="sxs-lookup"><span data-stu-id="f60b6-271">Implement the property accessors.</span></span> <span data-ttu-id="f60b6-272">Kontrolka `MarqueeBorder` ma kilka właściwości do kontrolowania jego wyglądu.</span><span class="sxs-lookup"><span data-stu-id="f60b6-272">The `MarqueeBorder` control has several properties for controlling its appearance.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]

11. <span data-ttu-id="f60b6-273">Zaimplementuj programy obsługi dla zdarzeń <xref:System.ComponentModel.BackgroundWorker.DoWork> i <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> składnika <xref:System.ComponentModel.BackgroundWorker>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-273">Implement the handlers for the <xref:System.ComponentModel.BackgroundWorker> component's <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> events.</span></span>

    <span data-ttu-id="f60b6-274">Procedura obsługi zdarzeń <xref:System.ComponentModel.BackgroundWorker.DoWork> uśpienia dla liczby milisekund określonych przez `UpdatePeriod` następnie wywołuje zdarzenie <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>, dopóki kod nie zatrzyma animacji przez wywołanie <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-274">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler sleeps for the number of milliseconds specified by `UpdatePeriod` then raises the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, until your code stops the animation by calling <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.</span></span>

    <span data-ttu-id="f60b6-275">Program obsługi zdarzeń <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> zwiększa położenie światła "Base", z którego jest określany stan światła/ciemnego innych sygnalizatorów, i wywołuje metodę <xref:System.Windows.Forms.Control.Refresh%2A>, aby spowodować, że formant będzie odświeżał sam siebie.</span><span class="sxs-lookup"><span data-stu-id="f60b6-275">The <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler increments the position of the "base" light, from which the light/dark state of the other lights is determined, and calls the <xref:System.Windows.Forms.Control.Refresh%2A> method to cause the control to repaint itself.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]

12. <span data-ttu-id="f60b6-276">Zaimplementuj metody pomocnika, `IsLit` i `DrawLight`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-276">Implement the helper methods, `IsLit` and `DrawLight`.</span></span>

    <span data-ttu-id="f60b6-277">Metoda `IsLit` określa kolor światła w danym położeniu.</span><span class="sxs-lookup"><span data-stu-id="f60b6-277">The `IsLit` method determines the color of a light at a given position.</span></span> <span data-ttu-id="f60b6-278">Światła "zapala się" są rysowane w kolorze podanym przez właściwość `LightColor`, a te, które są "ciemne" są rysowane w kolorze podanym przez właściwość `DarkColor`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-278">Lights that are "lit" are drawn in the color given by the `LightColor` property, and those that are "dark" are drawn in the color given by the `DarkColor` property.</span></span>

    <span data-ttu-id="f60b6-279">Metoda `DrawLight` rysuje oświetlenie przy użyciu odpowiedniego koloru, kształtu i pozycji.</span><span class="sxs-lookup"><span data-stu-id="f60b6-279">The `DrawLight` method draws a light using the appropriate color, shape, and position.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]

13. <span data-ttu-id="f60b6-280">Zastąp metody <xref:System.Windows.Forms.Control.OnLayout%2A> i <xref:System.Windows.Forms.Control.OnPaint%2A>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-280">Override the <xref:System.Windows.Forms.Control.OnLayout%2A> and <xref:System.Windows.Forms.Control.OnPaint%2A> methods.</span></span>

    <span data-ttu-id="f60b6-281">Metoda <xref:System.Windows.Forms.Control.OnPaint%2A> rysuje światła wzdłuż krawędzi kontrolki `MarqueeBorder`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-281">The <xref:System.Windows.Forms.Control.OnPaint%2A> method draws the lights along the edges of the `MarqueeBorder` control.</span></span>

    <span data-ttu-id="f60b6-282">Ponieważ metoda <xref:System.Windows.Forms.Control.OnPaint%2A> zależy od wymiarów kontrolki `MarqueeBorder`, należy wywołać ją za każdym razem, gdy zmieni się układ.</span><span class="sxs-lookup"><span data-stu-id="f60b6-282">Because the <xref:System.Windows.Forms.Control.OnPaint%2A> method depends on the dimensions of the `MarqueeBorder` control, you need to call it whenever the layout changes.</span></span> <span data-ttu-id="f60b6-283">Aby to osiągnąć, Zastąp <xref:System.Windows.Forms.Control.OnLayout%2A> i <xref:System.Windows.Forms.Control.Refresh%2A>wywołania.</span><span class="sxs-lookup"><span data-stu-id="f60b6-283">To achieve this, override <xref:System.Windows.Forms.Control.OnLayout%2A> and call <xref:System.Windows.Forms.Control.Refresh%2A>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]

## <a name="create-a-custom-designer-to-shadow-and-filter-properties"></a><span data-ttu-id="f60b6-284">Tworzenie projektanta niestandardowego dla właściwości cieni i filtru</span><span class="sxs-lookup"><span data-stu-id="f60b6-284">Create a Custom Designer to Shadow and Filter Properties</span></span>

<span data-ttu-id="f60b6-285">Klasa `MarqueeControlRootDesigner` dostarcza implementację głównego projektanta.</span><span class="sxs-lookup"><span data-stu-id="f60b6-285">The `MarqueeControlRootDesigner` class provides the implementation for the root designer.</span></span> <span data-ttu-id="f60b6-286">Oprócz tego projektanta, który działa na `MarqueeControl`, potrzebny będzie niestandardowy Projektant, który jest skojarzony z formantem `MarqueeBorder`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-286">In addition to this designer, which operates on the `MarqueeControl`, you'll need a custom designer that is specifically associated with the `MarqueeBorder` control.</span></span> <span data-ttu-id="f60b6-287">Ten Projektant udostępnia niestandardowe zachowanie odpowiednie w kontekście niestandardowego projektanta głównego.</span><span class="sxs-lookup"><span data-stu-id="f60b6-287">This designer provides custom behavior that is appropriate in the context of the custom root designer.</span></span>

<span data-ttu-id="f60b6-288">W konkretnym `MarqueeBorderDesigner` będzie "Shadow" i filtruje pewne właściwości kontrolki `MarqueeBorder`, zmieniając ich interakcje ze środowiskiem projektowym.</span><span class="sxs-lookup"><span data-stu-id="f60b6-288">Specifically, the `MarqueeBorderDesigner` will "shadow" and filter certain properties on the `MarqueeBorder` control, changing their interaction with the design environment.</span></span>

<span data-ttu-id="f60b6-289">Przechwycenie wywołań metody dostępu do właściwości jest znane jako "przesłanianie".</span><span class="sxs-lookup"><span data-stu-id="f60b6-289">Intercepting calls to a component's property accessor is known as "shadowing."</span></span> <span data-ttu-id="f60b6-290">Umożliwia projektantowi śledzenie wartości ustawionej przez użytkownika i opcjonalne przekazywanie tej wartości do zaprojektowanego składnika.</span><span class="sxs-lookup"><span data-stu-id="f60b6-290">It allows a designer to track the value set by the user and optionally pass that value to the component being designed.</span></span>

<span data-ttu-id="f60b6-291">Na potrzeby tego przykładu właściwości <xref:System.Windows.Forms.Control.Visible%2A> i <xref:System.Windows.Forms.Control.Enabled%2A> zostaną obsłonięte przez `MarqueeBorderDesigner`, co uniemożliwi użytkownikowi nieukrywanie lub wyłączenie kontrolki `MarqueeBorder` w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="f60b6-291">For this example, the <xref:System.Windows.Forms.Control.Visible%2A> and <xref:System.Windows.Forms.Control.Enabled%2A> properties will be shadowed by the `MarqueeBorderDesigner`, which prevents the user from making the `MarqueeBorder` control invisible or disabled during design time.</span></span>

<span data-ttu-id="f60b6-292">Projektanci mogą również dodawać i usuwać właściwości.</span><span class="sxs-lookup"><span data-stu-id="f60b6-292">Designers can also add and remove properties.</span></span> <span data-ttu-id="f60b6-293">W tym przykładzie właściwość <xref:System.Windows.Forms.Control.Padding%2A> zostanie usunięta w czasie projektowania, ponieważ kontrolka `MarqueeBorder` programowo ustawia uzupełnienie na podstawie rozmiaru świateł określonych przez właściwość `LightSize`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-293">For this example, the <xref:System.Windows.Forms.Control.Padding%2A> property will be removed at design time, because the `MarqueeBorder` control programmatically sets the padding based on the size of the lights specified by the `LightSize` property.</span></span>

<span data-ttu-id="f60b6-294">Klasa bazowa dla `MarqueeBorderDesigner` jest <xref:System.ComponentModel.Design.ComponentDesigner>, która ma metody, które mogą zmieniać atrybuty, właściwości i zdarzenia udostępniane przez formant w czasie projektowania:</span><span class="sxs-lookup"><span data-stu-id="f60b6-294">The base class for `MarqueeBorderDesigner` is <xref:System.ComponentModel.Design.ComponentDesigner>, which has methods that can change the attributes, properties, and events exposed by a control at design time:</span></span>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>

<span data-ttu-id="f60b6-295">Podczas zmiany interfejsu publicznego składnika przy użyciu tych metod wykonaj następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="f60b6-295">When changing the public interface of a component using these methods, follow these rules:</span></span>

- <span data-ttu-id="f60b6-296">Dodaj lub Usuń elementy tylko w `PreFilter` metodach</span><span class="sxs-lookup"><span data-stu-id="f60b6-296">Add or remove items in the `PreFilter` methods only</span></span>

- <span data-ttu-id="f60b6-297">Modyfikuj tylko istniejące elementy w metodach `PostFilter`</span><span class="sxs-lookup"><span data-stu-id="f60b6-297">Modify existing items in the `PostFilter` methods only</span></span>

- <span data-ttu-id="f60b6-298">Zawsze Wywołaj implementację bazową najpierw w metodach `PreFilter`</span><span class="sxs-lookup"><span data-stu-id="f60b6-298">Always call the base implementation first in the `PreFilter` methods</span></span>

- <span data-ttu-id="f60b6-299">Zawsze Wywołaj implementację podstawową jako ostatnią w metodach `PostFilter`</span><span class="sxs-lookup"><span data-stu-id="f60b6-299">Always call the base implementation last in the `PostFilter` methods</span></span>

<span data-ttu-id="f60b6-300">Przestrzeganie tych reguł zapewnia, że wszystkie projektanci w środowisku czasu projektowania mają spójny widok wszystkich składników, które są zaprojektowane.</span><span class="sxs-lookup"><span data-stu-id="f60b6-300">Adhering to these rules ensures that all designers in the design-time environment have a consistent view of all components being designed.</span></span>

<span data-ttu-id="f60b6-301">Klasa <xref:System.ComponentModel.Design.ComponentDesigner> zawiera słownik służący do zarządzania wartościami właściwości cieniowanych, co zwalnia konieczność tworzenia określonych zmiennych wystąpień.</span><span class="sxs-lookup"><span data-stu-id="f60b6-301">The <xref:System.ComponentModel.Design.ComponentDesigner> class provides a dictionary for managing the values of shadowed properties, which relieves you of the need to create specific instance variables.</span></span>

### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a><span data-ttu-id="f60b6-302">Aby utworzyć projektanta niestandardowego dla właściwości cieni i filtru</span><span class="sxs-lookup"><span data-stu-id="f60b6-302">To create a custom designer to shadow and filter properties</span></span>

1. <span data-ttu-id="f60b6-303">Kliknij prawym przyciskiem myszy folder **projekt** i Dodaj nową klasę.</span><span class="sxs-lookup"><span data-stu-id="f60b6-303">Right-click the **Design** folder and add a new class.</span></span> <span data-ttu-id="f60b6-304">Nadaj plikowi źródłowej podstawową nazwę **MarqueeBorderDesigner**.</span><span class="sxs-lookup"><span data-stu-id="f60b6-304">Give the source file a base name of **MarqueeBorderDesigner**.</span></span>

2. <span data-ttu-id="f60b6-305">Otwórz plik źródłowy MarqueeBorderDesigner w **edytorze kodu**.</span><span class="sxs-lookup"><span data-stu-id="f60b6-305">Open the MarqueeBorderDesigner source file in the **Code Editor**.</span></span> <span data-ttu-id="f60b6-306">W górnej części pliku Zaimportuj następujące przestrzenie nazw:</span><span class="sxs-lookup"><span data-stu-id="f60b6-306">At the top of the file, import the following namespaces:</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]

3. <span data-ttu-id="f60b6-307">Zmień deklarację `MarqueeBorderDesigner` na dziedziczenie z <xref:System.Windows.Forms.Design.ParentControlDesigner>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-307">Change the declaration of `MarqueeBorderDesigner` to inherit from <xref:System.Windows.Forms.Design.ParentControlDesigner>.</span></span>

    <span data-ttu-id="f60b6-308">Ponieważ kontrolka `MarqueeBorder` może zawierać kontrolki podrzędne, `MarqueeBorderDesigner` dziedziczy po <xref:System.Windows.Forms.Design.ParentControlDesigner>, który obsługuje interakcję nadrzędny-podrzędny.</span><span class="sxs-lookup"><span data-stu-id="f60b6-308">Because the `MarqueeBorder` control can contain child controls, `MarqueeBorderDesigner` inherits from <xref:System.Windows.Forms.Design.ParentControlDesigner>, which handles the parent-child interaction.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]

4. <span data-ttu-id="f60b6-309">Zastąp podstawową implementację <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-309">Override the base implementation of <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]

5. <span data-ttu-id="f60b6-310">Zaimplementuj właściwości <xref:System.Windows.Forms.Control.Enabled%2A> i <xref:System.Windows.Forms.Control.Visible%2A>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-310">Implement the <xref:System.Windows.Forms.Control.Enabled%2A> and <xref:System.Windows.Forms.Control.Visible%2A> properties.</span></span> <span data-ttu-id="f60b6-311">Te implementacje zasłaniają właściwości kontrolki.</span><span class="sxs-lookup"><span data-stu-id="f60b6-311">These implementations shadow the control's properties.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]

## <a name="handle-component-changes"></a><span data-ttu-id="f60b6-312">Obsługa zmian składników</span><span class="sxs-lookup"><span data-stu-id="f60b6-312">Handle Component Changes</span></span>

<span data-ttu-id="f60b6-313">Klasa `MarqueeControlRootDesigner` udostępnia niestandardowe środowisko czasu projektowania dla wystąpień `MarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-313">The `MarqueeControlRootDesigner` class provides the custom design-time experience for your `MarqueeControl` instances.</span></span> <span data-ttu-id="f60b6-314">Większość funkcji czasu projektowania jest dziedziczona z klasy <xref:System.Windows.Forms.Design.DocumentDesigner>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-314">Most of the design-time functionality is inherited from the <xref:System.Windows.Forms.Design.DocumentDesigner> class.</span></span> <span data-ttu-id="f60b6-315">Twój kod Zaimplementuj dwa specyficzne dostosowania: obsługa zmian składników i Dodawanie zleceń projektanta.</span><span class="sxs-lookup"><span data-stu-id="f60b6-315">Your code will implement two specific customizations: handling component changes, and adding designer verbs.</span></span>

<span data-ttu-id="f60b6-316">Podczas projektowania wystąpień `MarqueeControl` przez użytkowników Projektant główny będzie śledził zmiany w `MarqueeControl` i jego kontrolkach podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="f60b6-316">As users design their `MarqueeControl` instances, your root designer will track changes to the `MarqueeControl` and its child controls.</span></span> <span data-ttu-id="f60b6-317">Środowisko czasu projektowania oferuje wygodną usługę, <xref:System.ComponentModel.Design.IComponentChangeService>do śledzenia zmian stanu składnika.</span><span class="sxs-lookup"><span data-stu-id="f60b6-317">The design-time environment offers a convenient service, <xref:System.ComponentModel.Design.IComponentChangeService>, for tracking changes to component state.</span></span>

<span data-ttu-id="f60b6-318">Uzyskujesz odwołanie do tej usługi, badając środowisko przy użyciu metody <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-318">You acquire a reference to this service by querying the environment with the <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A> method.</span></span> <span data-ttu-id="f60b6-319">Jeśli zapytanie zakończyło się pomyślnie, Projektant może dołączyć procedurę obsługi dla zdarzenia <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> i wykonać wszelkie zadania wymagane do zapewnienia spójnego stanu w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="f60b6-319">If the query is successful, your designer can attach a handler for the <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> event and perform whatever tasks are required to maintain a consistent state at design time.</span></span>

<span data-ttu-id="f60b6-320">W przypadku klasy `MarqueeControlRootDesigner` należy wywołać metodę <xref:System.Windows.Forms.Control.Refresh%2A> dla każdego obiektu `IMarqueeWidget` zawartego w `MarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-320">In the case of the `MarqueeControlRootDesigner` class, you will call the <xref:System.Windows.Forms.Control.Refresh%2A> method on each `IMarqueeWidget` object contained by the `MarqueeControl`.</span></span> <span data-ttu-id="f60b6-321">Spowoduje to, że obiekt `IMarqueeWidget` ma być odpowiednio odświeżany, gdy zostaną zmienione właściwości, takie jak <xref:System.Windows.Forms.Control.Size%2A> elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="f60b6-321">This will cause the `IMarqueeWidget` object to repaint itself appropriately when properties like its parent's <xref:System.Windows.Forms.Control.Size%2A> are changed.</span></span>

### <a name="to-handle-component-changes"></a><span data-ttu-id="f60b6-322">Aby obsłużyć zmiany składników</span><span class="sxs-lookup"><span data-stu-id="f60b6-322">To handle component changes</span></span>

1. <span data-ttu-id="f60b6-323">Otwórz plik źródłowy `MarqueeControlRootDesigner` w **edytorze kodu** i Zastąp metodę <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-323">Open the `MarqueeControlRootDesigner` source file in the **Code Editor** and override the <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> method.</span></span> <span data-ttu-id="f60b6-324">Wywołaj podstawową implementację <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> i zapytania dla <xref:System.ComponentModel.Design.IComponentChangeService>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-324">Call the base implementation of <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> and query for the <xref:System.ComponentModel.Design.IComponentChangeService>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]

2. <span data-ttu-id="f60b6-325">Zaimplementuj procedurę obsługi zdarzeń <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-325">Implement the <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A> event handler.</span></span> <span data-ttu-id="f60b6-326">Przetestuj typ składnika wysyłającego, a jeśli jest to `IMarqueeWidget`, wywołaj jego <xref:System.Windows.Forms.Control.Refresh%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="f60b6-326">Test the sending component's type, and if it is an `IMarqueeWidget`, call its <xref:System.Windows.Forms.Control.Refresh%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]

## <a name="add-designer-verbs-to-your-custom-designer"></a><span data-ttu-id="f60b6-327">Dodawanie zleceń projektanta do projektanta niestandardowego</span><span class="sxs-lookup"><span data-stu-id="f60b6-327">Add Designer Verbs to your Custom Designer</span></span>

<span data-ttu-id="f60b6-328">Zlecenie projektanta jest poleceniem menu połączonym z programem obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f60b6-328">A designer verb is a menu command linked to an event handler.</span></span> <span data-ttu-id="f60b6-329">Zlecenia projektanta są dodawane do menu skrótów składnika w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="f60b6-329">Designer verbs are added to a component's shortcut menu at design time.</span></span> <span data-ttu-id="f60b6-330">Aby uzyskać więcej informacji, zobacz <xref:System.ComponentModel.Design.DesignerVerb>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-330">For more information, see <xref:System.ComponentModel.Design.DesignerVerb>.</span></span>

<span data-ttu-id="f60b6-331">Do projektantów zostaną dodane dwa zlecenia projektanta: **Uruchom test** i **Zatrzymaj test**.</span><span class="sxs-lookup"><span data-stu-id="f60b6-331">You will add two designer verbs to your designers: **Run Test** and **Stop Test**.</span></span> <span data-ttu-id="f60b6-332">Te czasowniki umożliwią wyświetlenie zachowania `MarqueeControl` w czasie wykonywania w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="f60b6-332">These verbs will allow you to view the run-time behavior of the `MarqueeControl` at design time.</span></span> <span data-ttu-id="f60b6-333">Te zlecenia zostaną dodane do `MarqueeControlRootDesigner`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-333">These verbs will be added to `MarqueeControlRootDesigner`.</span></span>

<span data-ttu-id="f60b6-334">Gdy jest wywoływany **Test Run** , program obsługi zdarzeń zlecenia wywoła metodę `StartMarquee` na `MarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-334">When **Run Test** is invoked, the verb event handler will call the `StartMarquee` method on the `MarqueeControl`.</span></span> <span data-ttu-id="f60b6-335">Po wywołaniu **testu zatrzymania** program obsługi zdarzeń zlecenia wywoła metodę `StopMarquee` w `MarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-335">When **Stop Test** is invoked, the verb event handler will call the `StopMarquee` method on the `MarqueeControl`.</span></span> <span data-ttu-id="f60b6-336">Implementacja metod `StartMarquee` i `StopMarquee` wywoływanie tych metod na zawartych kontrolkach, które implementują `IMarqueeWidget`, tak aby wszystkie zawarte kontrolki `IMarqueeWidget` również uczestniczyły w teście.</span><span class="sxs-lookup"><span data-stu-id="f60b6-336">The implementation of the `StartMarquee` and `StopMarquee` methods call these methods on contained controls that implement `IMarqueeWidget`, so any contained `IMarqueeWidget` controls will also participate in the test.</span></span>

### <a name="to-add-designer-verbs-to-your-custom-designers"></a><span data-ttu-id="f60b6-337">Aby dodać czasowniki projektanta do niestandardowych projektantów</span><span class="sxs-lookup"><span data-stu-id="f60b6-337">To add designer verbs to your custom designers</span></span>

1. <span data-ttu-id="f60b6-338">W klasie `MarqueeControlRootDesigner` Dodaj programy obsługi zdarzeń o nazwie `OnVerbRunTest` i `OnVerbStopTest`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-338">In the `MarqueeControlRootDesigner` class, add event handlers named `OnVerbRunTest` and `OnVerbStopTest`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]

2. <span data-ttu-id="f60b6-339">Połącz te programy obsługi zdarzeń z odpowiednimi zleceniami projektanta.</span><span class="sxs-lookup"><span data-stu-id="f60b6-339">Connect these event handlers to their corresponding designer verbs.</span></span> <span data-ttu-id="f60b6-340">`MarqueeControlRootDesigner` dziedziczy <xref:System.ComponentModel.Design.DesignerVerbCollection> z klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="f60b6-340">`MarqueeControlRootDesigner` inherits a <xref:System.ComponentModel.Design.DesignerVerbCollection> from its base class.</span></span> <span data-ttu-id="f60b6-341">Utworzysz dwa nowe obiekty <xref:System.ComponentModel.Design.DesignerVerb> i dodasz je do tej kolekcji w metodzie <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-341">You will create two new <xref:System.ComponentModel.Design.DesignerVerb> objects and add them to this collection in the <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> method.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]

## <a name="create-a-custom-uitypeeditor"></a><span data-ttu-id="f60b6-342">Tworzenie niestandardowego UITypeEditor</span><span class="sxs-lookup"><span data-stu-id="f60b6-342">Create a Custom UITypeEditor</span></span>

<span data-ttu-id="f60b6-343">Podczas tworzenia niestandardowego środowiska czasu projektowania dla użytkowników często pożądane jest utworzenie interakcji niestandardowej z okno Właściwości.</span><span class="sxs-lookup"><span data-stu-id="f60b6-343">When you create a custom design-time experience for users, it is often desirable to create a custom interaction with the Properties window.</span></span> <span data-ttu-id="f60b6-344">Można to zrobić, tworząc <xref:System.Drawing.Design.UITypeEditor>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-344">You can accomplish this by creating a <xref:System.Drawing.Design.UITypeEditor>.</span></span>

<span data-ttu-id="f60b6-345">Formant `MarqueeBorder` uwidacznia kilka właściwości w okno Właściwości.</span><span class="sxs-lookup"><span data-stu-id="f60b6-345">The `MarqueeBorder` control exposes several properties in the Properties window.</span></span> <span data-ttu-id="f60b6-346">Dwie z tych właściwości, `MarqueeSpinDirection` i `MarqueeLightShape` są reprezentowane przez wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="f60b6-346">Two of these properties, `MarqueeSpinDirection` and `MarqueeLightShape` are represented by enumerations.</span></span> <span data-ttu-id="f60b6-347">Aby zilustrować użycie edytora typów interfejsu użytkownika, właściwość `MarqueeLightShape` będzie miała skojarzoną klasę <xref:System.Drawing.Design.UITypeEditor>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-347">To illustrate the use of a UI type editor, the `MarqueeLightShape` property will have an associated <xref:System.Drawing.Design.UITypeEditor> class.</span></span>

### <a name="to-create-a-custom-ui-type-editor"></a><span data-ttu-id="f60b6-348">Aby utworzyć niestandardowy Edytor typów interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="f60b6-348">To create a custom UI type editor</span></span>

1. <span data-ttu-id="f60b6-349">Otwórz plik źródłowy `MarqueeBorder` w **edytorze kodu**.</span><span class="sxs-lookup"><span data-stu-id="f60b6-349">Open the `MarqueeBorder` source file in the **Code Editor**.</span></span>

2. <span data-ttu-id="f60b6-350">W definicji klasy `MarqueeBorder` deklaruj klasę o nazwie `LightShapeEditor`, która pochodzi z <xref:System.Drawing.Design.UITypeEditor>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-350">In the definition of the `MarqueeBorder` class, declare a class called `LightShapeEditor` that derives from <xref:System.Drawing.Design.UITypeEditor>.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]

3. <span data-ttu-id="f60b6-351">Zadeklaruj zmienną wystąpienia <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> o nazwie `editorService`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-351">Declare an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance variable called `editorService`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]

4. <span data-ttu-id="f60b6-352">Zastąp metodę <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-352">Override the <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> method.</span></span> <span data-ttu-id="f60b6-353">Ta implementacja zwraca <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, co informuje środowisko projektowe o sposobie wyświetlania `LightShapeEditor`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-353">This implementation returns <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, which tells the design environment how to display the `LightShapeEditor`.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]

5. <span data-ttu-id="f60b6-354">Zastąp metodę <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-354">Override the <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> method.</span></span> <span data-ttu-id="f60b6-355">Ta implementacja wysyła zapytanie do środowiska projektowego dla obiektu <xref:System.Windows.Forms.Design.IWindowsFormsEditorService>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-355">This implementation queries the design environment for an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> object.</span></span> <span data-ttu-id="f60b6-356">W przypadku pomyślnego utworzenia `LightShapeSelectionControl`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-356">If successful, it creates a `LightShapeSelectionControl`.</span></span> <span data-ttu-id="f60b6-357">Metoda <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> jest wywoływana w celu uruchomienia `LightShapeEditor`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-357">The <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> method is invoked to start the `LightShapeEditor`.</span></span> <span data-ttu-id="f60b6-358">Wartość zwracana z tego wywołania jest zwracana do środowiska projektowego.</span><span class="sxs-lookup"><span data-stu-id="f60b6-358">The return value from this invocation is returned to the design environment.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]

## <a name="create-a-view-control-for-your-custom-uitypeeditor"></a><span data-ttu-id="f60b6-359">Tworzenie kontrolki widoku dla niestandardowego UITypeEditor</span><span class="sxs-lookup"><span data-stu-id="f60b6-359">Create a View Control for your Custom UITypeEditor</span></span>

<span data-ttu-id="f60b6-360">Właściwość `MarqueeLightShape` obsługuje dwa typy świateł: `Square` i `Circle`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-360">The `MarqueeLightShape` property supports two types of light shapes: `Square` and `Circle`.</span></span> <span data-ttu-id="f60b6-361">Utworzysz kontrolkę niestandardową używaną wyłącznie na potrzeby graficznego wyświetlania tych wartości w okno Właściwości.</span><span class="sxs-lookup"><span data-stu-id="f60b6-361">You will create a custom control used solely for the purpose of graphically displaying these values in the Properties window.</span></span> <span data-ttu-id="f60b6-362">Ta kontrolka niestandardowa będzie używana przez <xref:System.Drawing.Design.UITypeEditor> do korzystania z okno Właściwości.</span><span class="sxs-lookup"><span data-stu-id="f60b6-362">This custom control will be used by your <xref:System.Drawing.Design.UITypeEditor> to interact with the Properties window.</span></span>

### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a><span data-ttu-id="f60b6-363">Aby utworzyć kontrolkę widoku dla niestandardowego edytora typów interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="f60b6-363">To create a view control for your custom UI type editor</span></span>

1. <span data-ttu-id="f60b6-364">Dodaj nowy element <xref:System.Windows.Forms.UserControl> do projektu `MarqueeControlLibrary`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-364">Add a new <xref:System.Windows.Forms.UserControl> item to the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="f60b6-365">Nadaj nowemu plikowi źródłowej nazwę bazową **LightShapeSelectionControl**.</span><span class="sxs-lookup"><span data-stu-id="f60b6-365">Give the new source file a base name of **LightShapeSelectionControl**.</span></span>

2. <span data-ttu-id="f60b6-366">Przeciągnij dwie <xref:System.Windows.Forms.Panel> kontrolki z **przybornika** na `LightShapeSelectionControl`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-366">Drag two <xref:System.Windows.Forms.Panel> controls from the **Toolbox** onto the `LightShapeSelectionControl`.</span></span> <span data-ttu-id="f60b6-367">Nadaj mu nazwę `squarePanel` i `circlePanel`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-367">Name them `squarePanel` and `circlePanel`.</span></span> <span data-ttu-id="f60b6-368">Rozmieść je obok siebie.</span><span class="sxs-lookup"><span data-stu-id="f60b6-368">Arrange them side by side.</span></span> <span data-ttu-id="f60b6-369">Ustaw właściwość <xref:System.Windows.Forms.Control.Size%2A> obu <xref:System.Windows.Forms.Panel> formantów na **(60, 60)** .</span><span class="sxs-lookup"><span data-stu-id="f60b6-369">Set the <xref:System.Windows.Forms.Control.Size%2A> property of both <xref:System.Windows.Forms.Panel> controls to **(60, 60)**.</span></span> <span data-ttu-id="f60b6-370">Ustaw właściwość <xref:System.Windows.Forms.Control.Location%2A> kontrolki `squarePanel` na **(8, 10)** .</span><span class="sxs-lookup"><span data-stu-id="f60b6-370">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the `squarePanel` control to **(8, 10)**.</span></span> <span data-ttu-id="f60b6-371">Ustaw właściwość <xref:System.Windows.Forms.Control.Location%2A> kontrolki `circlePanel` na **(80, 10)** .</span><span class="sxs-lookup"><span data-stu-id="f60b6-371">Set the <xref:System.Windows.Forms.Control.Location%2A> property of the `circlePanel` control to **(80, 10)**.</span></span> <span data-ttu-id="f60b6-372">Na koniec ustaw właściwość <xref:System.Windows.Forms.Control.Size%2A> `LightShapeSelectionControl` na wartość **(150, 80)** .</span><span class="sxs-lookup"><span data-stu-id="f60b6-372">Finally, set the <xref:System.Windows.Forms.Control.Size%2A> property of the `LightShapeSelectionControl` to **(150, 80)**.</span></span>

3. <span data-ttu-id="f60b6-373">Otwórz plik źródłowy `LightShapeSelectionControl` w **edytorze kodu**.</span><span class="sxs-lookup"><span data-stu-id="f60b6-373">Open the `LightShapeSelectionControl` source file in the **Code Editor**.</span></span> <span data-ttu-id="f60b6-374">W górnej części pliku zaimportuj <xref:System.Windows.Forms.Design?displayProperty=nameWithType> przestrzeń nazw:</span><span class="sxs-lookup"><span data-stu-id="f60b6-374">At the top of the file, import the <xref:System.Windows.Forms.Design?displayProperty=nameWithType> namespace:</span></span>

   ```vb
   Imports System.Windows.Forms.Design
   ```

   ```csharp
   using System.Windows.Forms.Design;
   ```

4. <span data-ttu-id="f60b6-375">Zaimplementuj obsługę zdarzeń <xref:System.Windows.Forms.Control.Click> dla kontrolek `squarePanel` i `circlePanel`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-375">Implement <xref:System.Windows.Forms.Control.Click> event handlers for the `squarePanel` and `circlePanel` controls.</span></span> <span data-ttu-id="f60b6-376">Te metody wywołują <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A>, aby zakończyć sesję niestandardowego <xref:System.Drawing.Design.UITypeEditor> edycji.</span><span class="sxs-lookup"><span data-stu-id="f60b6-376">These methods invoke <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> to end the custom <xref:System.Drawing.Design.UITypeEditor> editing session.</span></span>

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]

5. <span data-ttu-id="f60b6-377">Zadeklaruj zmienną wystąpienia <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> o nazwie `editorService`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-377">Declare an <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> instance variable called `editorService`.</span></span>

   ```vb
   Private editorService As IWindowsFormsEditorService
   ```

   ```csharp
   private IWindowsFormsEditorService editorService;
   ```

6. <span data-ttu-id="f60b6-378">Zadeklaruj zmienną wystąpienia `MarqueeLightShape` o nazwie `lightShapeValue`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-378">Declare a `MarqueeLightShape` instance variable called `lightShapeValue`.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]

7. <span data-ttu-id="f60b6-379">W konstruktorze `LightShapeSelectionControl` Dołącz obsługę zdarzeń <xref:System.Windows.Forms.Control.Click> do `squarePanel` i `circlePanel` formantów <xref:System.Windows.Forms.Control.Click>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-379">In the `LightShapeSelectionControl` constructor, attach the <xref:System.Windows.Forms.Control.Click> event handlers to the `squarePanel` and `circlePanel` controls' <xref:System.Windows.Forms.Control.Click> events.</span></span> <span data-ttu-id="f60b6-380">Ponadto Zdefiniuj przeciążenie konstruktora, które przypisuje wartość `MarqueeLightShape` ze środowiska projektowego do pola `lightShapeValue`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-380">Also, define a constructor overload that assigns the `MarqueeLightShape` value from the design environment to the `lightShapeValue` field.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]

8. <span data-ttu-id="f60b6-381">W <xref:System.ComponentModel.Component.Dispose%2A> metodzie Odłącz <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f60b6-381">In the <xref:System.ComponentModel.Component.Dispose%2A> method, detach the <xref:System.Windows.Forms.Control.Click> event handlers.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]

9. <span data-ttu-id="f60b6-382">W **Eksplorator rozwiązań**kliknij przycisk **Pokaż wszystkie pliki** .</span><span class="sxs-lookup"><span data-stu-id="f60b6-382">In **Solution Explorer**, click the **Show All Files** button.</span></span> <span data-ttu-id="f60b6-383">Otwórz plik LightShapeSelectionControl.Designer.cs lub LightShapeSelectionControl. Designer. vb i usuń definicję domyślną metody <xref:System.ComponentModel.Component.Dispose%2A>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-383">Open the LightShapeSelectionControl.Designer.cs or LightShapeSelectionControl.Designer.vb file, and remove the default definition of the <xref:System.ComponentModel.Component.Dispose%2A> method.</span></span>

10. <span data-ttu-id="f60b6-384">Zaimplementuj Właściwość `LightShape`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-384">Implement the `LightShape` property.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]

11. <span data-ttu-id="f60b6-385">Zastąp metodę <xref:System.Windows.Forms.Control.OnPaint%2A>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-385">Override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="f60b6-386">Ta implementacja spowoduje narysowanie wypełnionego kwadratu i okręgu.</span><span class="sxs-lookup"><span data-stu-id="f60b6-386">This implementation will draw a filled square and circle.</span></span> <span data-ttu-id="f60b6-387">Zostanie również wyświetlona wybrana wartość przez narysowanie obramowania wokół jednego kształtu lub drugiego.</span><span class="sxs-lookup"><span data-stu-id="f60b6-387">It will also highlight the selected value by drawing a border around one shape or the other.</span></span>

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]

## <a name="test-your-custom-control-in-the-designer"></a><span data-ttu-id="f60b6-388">Testowanie kontrolki niestandardowej w projektancie</span><span class="sxs-lookup"><span data-stu-id="f60b6-388">Test your Custom Control in the Designer</span></span>

<span data-ttu-id="f60b6-389">W tym momencie można skompilować projekt `MarqueeControlLibrary`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-389">At this point, you can build the `MarqueeControlLibrary` project.</span></span> <span data-ttu-id="f60b6-390">Przetestuj swoją implementację, tworząc kontrolkę, która dziedziczy z klasy `MarqueeControl` i korzystając z niej w formularzu.</span><span class="sxs-lookup"><span data-stu-id="f60b6-390">Test your implementation by creating a control that inherits from the `MarqueeControl` class and using it on a form.</span></span>

### <a name="to-create-a-custom-marqueecontrol-implementation"></a><span data-ttu-id="f60b6-391">Aby utworzyć niestandardową implementację MarqueeControl</span><span class="sxs-lookup"><span data-stu-id="f60b6-391">To create a custom MarqueeControl implementation</span></span>

1. <span data-ttu-id="f60b6-392">Otwórz `DemoMarqueeControl` w Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="f60b6-392">Open `DemoMarqueeControl` in the Windows Forms Designer.</span></span> <span data-ttu-id="f60b6-393">Spowoduje to utworzenie wystąpienia typu `DemoMarqueeControl` i wyświetlenie go w wystąpieniu typu `MarqueeControlRootDesigner`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-393">This creates an instance of the `DemoMarqueeControl` type and displays it in an instance of the `MarqueeControlRootDesigner` type.</span></span>

2. <span data-ttu-id="f60b6-394">W **przyborniku**Otwórz kartę **składniki MarqueeControlLibrary** . Zobaczysz kontrolki `MarqueeBorder` i `MarqueeText` dostępne do wyboru.</span><span class="sxs-lookup"><span data-stu-id="f60b6-394">In the **Toolbox**, open the **MarqueeControlLibrary Components** tab. You will see the `MarqueeBorder` and `MarqueeText` controls available for selection.</span></span>

3. <span data-ttu-id="f60b6-395">Przeciągnij wystąpienie kontrolki `MarqueeBorder` na powierzchnię projektową `DemoMarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-395">Drag an instance of the `MarqueeBorder` control onto the `DemoMarqueeControl` design surface.</span></span> <span data-ttu-id="f60b6-396">Zadokuj tę `MarqueeBorder` kontrolkę do kontrolki nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="f60b6-396">Dock this `MarqueeBorder` control to the parent control.</span></span>

4. <span data-ttu-id="f60b6-397">Przeciągnij wystąpienie kontrolki `MarqueeText` na powierzchnię projektową `DemoMarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-397">Drag an instance of the `MarqueeText` control onto the `DemoMarqueeControl` design surface.</span></span>

5. <span data-ttu-id="f60b6-398">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="f60b6-398">Build the solution.</span></span>

6. <span data-ttu-id="f60b6-399">Kliknij prawym przyciskiem myszy `DemoMarqueeControl` i z menu skrótów wybierz opcję **Uruchom test** , aby rozpocząć animację.</span><span class="sxs-lookup"><span data-stu-id="f60b6-399">Right-click the `DemoMarqueeControl` and from the shortcut menu select the **Run Test** option to start the animation.</span></span> <span data-ttu-id="f60b6-400">Kliknij przycisk **Zatrzymaj test** , aby zatrzymać animację.</span><span class="sxs-lookup"><span data-stu-id="f60b6-400">Click **Stop Test** to stop the animation.</span></span>

7. <span data-ttu-id="f60b6-401">Otwórz **formularz Form1** w widok Projekt.</span><span class="sxs-lookup"><span data-stu-id="f60b6-401">Open **Form1** in Design view.</span></span>

8. <span data-ttu-id="f60b6-402">Umieść dwa <xref:System.Windows.Forms.Button> kontrolki w formularzu.</span><span class="sxs-lookup"><span data-stu-id="f60b6-402">Place two <xref:System.Windows.Forms.Button> controls on the form.</span></span> <span data-ttu-id="f60b6-403">Nadaj mu nazwę `startButton` i `stopButton`i Zmień <xref:System.Windows.Forms.Control.Text%2A> wartości właściwości tak, aby odpowiednio **uruchamiać** i **zatrzymywać**.</span><span class="sxs-lookup"><span data-stu-id="f60b6-403">Name them `startButton` and `stopButton`, and change the <xref:System.Windows.Forms.Control.Text%2A> property values to **Start** and **Stop**, respectively.</span></span>

9. <span data-ttu-id="f60b6-404">Zaimplementuj obsługę zdarzeń <xref:System.Windows.Forms.Control.Click> dla obu formantów <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="f60b6-404">Implement <xref:System.Windows.Forms.Control.Click> event handlers for both <xref:System.Windows.Forms.Button> controls.</span></span>

10. <span data-ttu-id="f60b6-405">W **przyborniku**Otwórz kartę **składniki MarqueeControlTest** . Zobaczysz `DemoMarqueeControl` dostępne do wyboru.</span><span class="sxs-lookup"><span data-stu-id="f60b6-405">In the **Toolbox**, open the **MarqueeControlTest Components** tab. You will see the `DemoMarqueeControl` available for selection.</span></span>

11. <span data-ttu-id="f60b6-406">Przeciągnij wystąpienie `DemoMarqueeControl` na powierzchnię projektu **Form1** .</span><span class="sxs-lookup"><span data-stu-id="f60b6-406">Drag an instance of `DemoMarqueeControl` onto the **Form1** design surface.</span></span>

12. <span data-ttu-id="f60b6-407">W obsłudze zdarzeń <xref:System.Windows.Forms.Control.Click> wywołaj metody `Start` i `Stop` na `DemoMarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-407">In the <xref:System.Windows.Forms.Control.Click> event handlers, invoke the `Start` and `Stop` methods on the `DemoMarqueeControl`.</span></span>

    ```vb
    Private Sub startButton_Click(sender As Object, e As System.EventArgs)
        Me.demoMarqueeControl1.Start()
    End Sub 'startButton_Click

    Private Sub stopButton_Click(sender As Object, e As System.EventArgs)
    Me.demoMarqueeControl1.Stop()
    End Sub 'stopButton_Click
    ```

    ```csharp
    private void startButton_Click(object sender, System.EventArgs e)
    {
        this.demoMarqueeControl1.Start();
    }

    private void stopButton_Click(object sender, System.EventArgs e)
    {
        this.demoMarqueeControl1.Stop();
    }
    ```

13. <span data-ttu-id="f60b6-408">Ustaw projekt `MarqueeControlTest` jako projekt startowy i uruchom go.</span><span class="sxs-lookup"><span data-stu-id="f60b6-408">Set the `MarqueeControlTest` project as the startup project and run it.</span></span> <span data-ttu-id="f60b6-409">Zobaczysz formularz wyświetlający `DemoMarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-409">You will see the form displaying your `DemoMarqueeControl`.</span></span> <span data-ttu-id="f60b6-410">Wybierz przycisk **Start** , aby rozpocząć animację.</span><span class="sxs-lookup"><span data-stu-id="f60b6-410">Select the **Start** button to start the animation.</span></span> <span data-ttu-id="f60b6-411">Powinieneś zobaczyć migający tekst i sygnalizatory poruszające się wokół obramowania.</span><span class="sxs-lookup"><span data-stu-id="f60b6-411">You should see the text flashing and the lights moving around the border.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f60b6-412">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="f60b6-412">Next steps</span></span>

<span data-ttu-id="f60b6-413">`MarqueeControlLibrary` ilustruje prostą implementację formantów niestandardowych i skojarzonych projektantów.</span><span class="sxs-lookup"><span data-stu-id="f60b6-413">The `MarqueeControlLibrary` demonstrates a simple implementation of custom controls and associated designers.</span></span> <span data-ttu-id="f60b6-414">Ten przykład można zwiększyć na kilka sposobów:</span><span class="sxs-lookup"><span data-stu-id="f60b6-414">You can make this sample more sophisticated in several ways:</span></span>

- <span data-ttu-id="f60b6-415">Zmień wartości właściwości `DemoMarqueeControl` w projektancie.</span><span class="sxs-lookup"><span data-stu-id="f60b6-415">Change the property values for the `DemoMarqueeControl` in the designer.</span></span> <span data-ttu-id="f60b6-416">Dodaj więcej formantów `MarqueBorder` i Zadokuj je w wystąpieniach nadrzędnych, aby utworzyć efekt zagnieżdżony.</span><span class="sxs-lookup"><span data-stu-id="f60b6-416">Add more `MarqueBorder` controls and dock them within their parent instances to create a nested effect.</span></span> <span data-ttu-id="f60b6-417">Eksperymentuj z różnymi ustawieniami `UpdatePeriod` i właściwościami jasnymi.</span><span class="sxs-lookup"><span data-stu-id="f60b6-417">Experiment with different settings for the `UpdatePeriod` and the light-related properties.</span></span>

- <span data-ttu-id="f60b6-418">Twórz własne implementacje `IMarqueeWidget`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-418">Author your own implementations of `IMarqueeWidget`.</span></span> <span data-ttu-id="f60b6-419">Można na przykład utworzyć migający znak "neon" lub animowany znak z wieloma obrazami.</span><span class="sxs-lookup"><span data-stu-id="f60b6-419">You could, for example, create a flashing "neon sign" or an animated sign with multiple images.</span></span>

- <span data-ttu-id="f60b6-420">Dalsze dostosowywanie środowiska czasu projektowania.</span><span class="sxs-lookup"><span data-stu-id="f60b6-420">Further customize the design-time experience.</span></span> <span data-ttu-id="f60b6-421">Możesz wypróbować więcej właściwości niż <xref:System.Windows.Forms.Control.Enabled%2A> i <xref:System.Windows.Forms.Control.Visible%2A>i dodać nowe właściwości.</span><span class="sxs-lookup"><span data-stu-id="f60b6-421">You could try shadowing more properties than <xref:System.Windows.Forms.Control.Enabled%2A> and <xref:System.Windows.Forms.Control.Visible%2A>, and you could add new properties.</span></span> <span data-ttu-id="f60b6-422">Dodaj nowe czasowniki projektanta, aby uprościć typowe zadania, takie jak dokowanie formantów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="f60b6-422">Add new designer verbs to simplify common tasks like docking child controls.</span></span>

- <span data-ttu-id="f60b6-423">Licencjonowanie `MarqueeControl`.</span><span class="sxs-lookup"><span data-stu-id="f60b6-423">License the `MarqueeControl`.</span></span>

- <span data-ttu-id="f60b6-424">Kontroluj sposób serializacji formantów i sposób generowania kodu.</span><span class="sxs-lookup"><span data-stu-id="f60b6-424">Control how your controls are serialized and how code is generated for them.</span></span> <span data-ttu-id="f60b6-425">Aby uzyskać więcej informacji, zobacz [dynamiczne generowanie kodu źródłowego i kompilacja](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="f60b6-425">For more information, see [Dynamic Source Code Generation and Compilation](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f60b6-426">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f60b6-426">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Design.ParentControlDesigner>
- <xref:System.Windows.Forms.Design.DocumentDesigner>
- <xref:System.ComponentModel.Design.IRootDesigner>
- <xref:System.ComponentModel.Design.DesignerVerb>
- <xref:System.Drawing.Design.UITypeEditor>
- <xref:System.ComponentModel.BackgroundWorker>
