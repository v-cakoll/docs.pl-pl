---
title: 'Przewodnik: tworzenie profesjonalnej kontrolki ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- toolbars [Windows Forms], walkthroughs
- ToolStrip control [Windows Forms], creating professionally styled controls
ms.assetid: b52339ae-f1d3-494e-996e-eb455614098a
ms.openlocfilehash: 226e805d0240236899ee0cc290f1060a3b0aa391
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211767"
---
# <a name="walkthrough-creating-a-professionally-styled-toolstrip-control"></a><span data-ttu-id="be483-102">Przewodnik: tworzenie profesjonalnej kontrolki ToolStrip</span><span class="sxs-lookup"><span data-stu-id="be483-102">Walkthrough: Creating a Professionally Styled ToolStrip Control</span></span>

<span data-ttu-id="be483-103">Możesz nadać aplikacji <xref:System.Windows.Forms.ToolStrip> kontroluje profesjonalny wygląd i zachowanie, pisząc własne klasy pochodzącej od <xref:System.Windows.Forms.ToolStripProfessionalRenderer> typu.</span><span class="sxs-lookup"><span data-stu-id="be483-103">You can give your application’s <xref:System.Windows.Forms.ToolStrip> controls a professional appearance and behavior by writing your own class derived from the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.</span></span>

<span data-ttu-id="be483-104">W tym instruktażu przedstawiono sposób użycia <xref:System.Windows.Forms.ToolStrip> formantów, aby utworzyć formant złożony, który przypomina **okienka nawigacji** udostępniane przez Microsoft Outlook®.</span><span class="sxs-lookup"><span data-stu-id="be483-104">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStrip> controls to create a composite control that resembles the **Navigation Pane** provided by Microsoft® Outlook®.</span></span> <span data-ttu-id="be483-105">Następujące zadania są przedstawione w niniejszym przewodniku:</span><span class="sxs-lookup"><span data-stu-id="be483-105">The following tasks are illustrated in this walkthrough:</span></span>

- <span data-ttu-id="be483-106">Tworzenie projektu Biblioteka formantów Windows.</span><span class="sxs-lookup"><span data-stu-id="be483-106">Creating a Windows Control Library project.</span></span>

- <span data-ttu-id="be483-107">Projektowanie kontrolki StackView.</span><span class="sxs-lookup"><span data-stu-id="be483-107">Designing the StackView Control.</span></span>

- <span data-ttu-id="be483-108">Implementowanie niestandardowego modułu renderowania.</span><span class="sxs-lookup"><span data-stu-id="be483-108">Implementing a Custom Renderer.</span></span>

<span data-ttu-id="be483-109">Gdy skończysz, konieczne będzie formantu wielokrotnego niestandardowe klienta za pomocą profesjonalny wygląd kontrolki Microsoft Office® XP.</span><span class="sxs-lookup"><span data-stu-id="be483-109">When you are finished, you will have a reusable custom client control with the professional appearance of a Microsoft Office® XP control.</span></span>

<span data-ttu-id="be483-110">Aby skopiować kod, w tym temacie na jednej liście, zobacz [jak: Tworzenie profesjonalnego formantu ToolStrip](how-to-create-a-professionally-styled-toolstrip-control.md).</span><span class="sxs-lookup"><span data-stu-id="be483-110">To copy the code in this topic as a single listing, see [How to: Create a Professionally Styled ToolStrip Control](how-to-create-a-professionally-styled-toolstrip-control.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="be483-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="be483-111">Prerequisites</span></span>

<span data-ttu-id="be483-112">Visual Studio w celu przeprowadzenia tego instruktażu jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="be483-112">You'll need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-control-library-project"></a><span data-ttu-id="be483-113">Utwórz projekt Biblioteka formantów</span><span class="sxs-lookup"><span data-stu-id="be483-113">Create the control library project</span></span>

1. <span data-ttu-id="be483-114">W programie Visual Studio Utwórz nowy projekt Biblioteka formantów Windows o nazwie `StackViewLibrary`.</span><span class="sxs-lookup"><span data-stu-id="be483-114">In Visual Studio, create a new Windows Control Library project named `StackViewLibrary`.</span></span>

2. <span data-ttu-id="be483-115">W **Eksploratora rozwiązań**, usunąć projekt domyślny formant przez usunięcie pliku źródłowego o nazwie "UserControl1.cs" lub "UserControl1.vb", w zależności od tego, w wybranym języku.</span><span class="sxs-lookup"><span data-stu-id="be483-115">In **Solution Explorer**, delete the project's default control by deleting the source file named "UserControl1.cs" or "UserControl1.vb", depending on your language of choice.</span></span>

     <span data-ttu-id="be483-116">Aby uzyskać więcej informacji, zobacz [jak: Usuń Delete i wykluczyć elementy](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="be483-116">For more information, see [How to: Remove, Delete, and Exclude Items](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100)).</span></span>

3. <span data-ttu-id="be483-117">Dodaj nową <xref:System.Windows.Forms.UserControl> elementu do **StackViewLibrary** projektu.</span><span class="sxs-lookup"><span data-stu-id="be483-117">Add a new <xref:System.Windows.Forms.UserControl> item to the **StackViewLibrary** project.</span></span> <span data-ttu-id="be483-118">Nazwij nowy plik źródłowy podstawowej z `StackView`.</span><span class="sxs-lookup"><span data-stu-id="be483-118">Give the new source file a base name of `StackView`.</span></span>

## <a name="design-the-stackview-control"></a><span data-ttu-id="be483-119">Projektowanie kontrolki StackView</span><span class="sxs-lookup"><span data-stu-id="be483-119">Design the StackView control</span></span>

<span data-ttu-id="be483-120">`StackView` Kontrolka jest kontrolką złożoną z jeden element podrzędny <xref:System.Windows.Forms.ToolStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="be483-120">The `StackView` control is a composite control with one child <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="be483-121">Aby uzyskać więcej informacji na temat formanty złożone zobacz [różne typy kontrolek niestandardowych](varieties-of-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="be483-121">For more information about composite controls, see [Varieties of Custom Controls](varieties-of-custom-controls.md).</span></span>

1. <span data-ttu-id="be483-122">Z **przybornika**, przeciągnij <xref:System.Windows.Forms.ToolStrip> kontrolki na powierzchnię projektową.</span><span class="sxs-lookup"><span data-stu-id="be483-122">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStrip> control to the design surface.</span></span>

2. <span data-ttu-id="be483-123">W **właściwości** oknie <xref:System.Windows.Forms.ToolStrip> właściwości formantu, zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="be483-123">In the **Properties** window, set the <xref:System.Windows.Forms.ToolStrip> control's properties according to the following table.</span></span>

    |<span data-ttu-id="be483-124">Właściwość</span><span class="sxs-lookup"><span data-stu-id="be483-124">Property</span></span>|<span data-ttu-id="be483-125">Wartość</span><span class="sxs-lookup"><span data-stu-id="be483-125">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="be483-126">Nazwa</span><span class="sxs-lookup"><span data-stu-id="be483-126">Name</span></span>|`stackStrip`|
    |<span data-ttu-id="be483-127">CanOverflow</span><span class="sxs-lookup"><span data-stu-id="be483-127">CanOverflow</span></span>|`false`|
    |<span data-ttu-id="be483-128">Dock</span><span class="sxs-lookup"><span data-stu-id="be483-128">Dock</span></span>|<xref:System.Windows.Forms.DockStyle.Bottom>|
    |<span data-ttu-id="be483-129">Czcionka</span><span class="sxs-lookup"><span data-stu-id="be483-129">Font</span></span>|`Tahoma, 10pt, style=Bold`|
    |<span data-ttu-id="be483-130">GripStyle</span><span class="sxs-lookup"><span data-stu-id="be483-130">GripStyle</span></span>|<xref:System.Windows.Forms.ToolStripGripStyle.Hidden>|
    |<span data-ttu-id="be483-131">LayoutStyle</span><span class="sxs-lookup"><span data-stu-id="be483-131">LayoutStyle</span></span>|<xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>|
    |<span data-ttu-id="be483-132">Dopełnienie</span><span class="sxs-lookup"><span data-stu-id="be483-132">Padding</span></span>|`0, 7, 0, 0`|
    |<span data-ttu-id="be483-133">RenderMode</span><span class="sxs-lookup"><span data-stu-id="be483-133">RenderMode</span></span>|<xref:System.Windows.Forms.ToolStripRenderMode.Professional>|

3. <span data-ttu-id="be483-134">W programie Windows Forms Designer kliknij <xref:System.Windows.Forms.ToolStrip> kontrolki **Dodaj** przycisku i Dodaj <xref:System.Windows.Forms.ToolStripButton> do `stackStrip` kontroli.</span><span class="sxs-lookup"><span data-stu-id="be483-134">In the Windows Forms Designer, click the <xref:System.Windows.Forms.ToolStrip> control's **Add** button and add a <xref:System.Windows.Forms.ToolStripButton> to the `stackStrip` control.</span></span>

4. <span data-ttu-id="be483-135">W **właściwości** oknie <xref:System.Windows.Forms.ToolStripButton> właściwości formantu, zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="be483-135">In the **Properties** window, set the <xref:System.Windows.Forms.ToolStripButton> control's properties according to the following table.</span></span>

    |<span data-ttu-id="be483-136">Właściwość</span><span class="sxs-lookup"><span data-stu-id="be483-136">Property</span></span>|<span data-ttu-id="be483-137">Wartość</span><span class="sxs-lookup"><span data-stu-id="be483-137">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="be483-138">Nazwa</span><span class="sxs-lookup"><span data-stu-id="be483-138">Name</span></span>|`mailStackButton`|
    |<span data-ttu-id="be483-139">CheckOnClick</span><span class="sxs-lookup"><span data-stu-id="be483-139">CheckOnClick</span></span>|<span data-ttu-id="be483-140">true</span><span class="sxs-lookup"><span data-stu-id="be483-140">true</span></span>|
    |<span data-ttu-id="be483-141">Wartość CheckState</span><span class="sxs-lookup"><span data-stu-id="be483-141">CheckState</span></span>|<xref:System.Windows.Forms.CheckState.Checked>|
    |<span data-ttu-id="be483-142">DisplayStyle</span><span class="sxs-lookup"><span data-stu-id="be483-142">DisplayStyle</span></span>|<xref:System.Windows.Forms.ToolStripItemDisplayStyle.ImageAndText>|
    |<span data-ttu-id="be483-143">ImageAlign</span><span class="sxs-lookup"><span data-stu-id="be483-143">ImageAlign</span></span>|<xref:System.Drawing.ContentAlignment.MiddleLeft>|
    |<span data-ttu-id="be483-144">ImageScaling</span><span class="sxs-lookup"><span data-stu-id="be483-144">ImageScaling</span></span>|<xref:System.Windows.Forms.ToolStripItemImageScaling.None>|
    |<span data-ttu-id="be483-145">ImageTransparentColor</span><span class="sxs-lookup"><span data-stu-id="be483-145">ImageTransparentColor</span></span>|`238, 238, 238`|
    |<span data-ttu-id="be483-146">Margines</span><span class="sxs-lookup"><span data-stu-id="be483-146">Margin</span></span>|`0, 0, 0, 0`|
    |<span data-ttu-id="be483-147">Dopełnienie</span><span class="sxs-lookup"><span data-stu-id="be483-147">Padding</span></span>|`3, 3, 3, 3`|
    |<span data-ttu-id="be483-148">Tekst</span><span class="sxs-lookup"><span data-stu-id="be483-148">Text</span></span>|<span data-ttu-id="be483-149">**wiadomości e-mail**</span><span class="sxs-lookup"><span data-stu-id="be483-149">**Mail**</span></span>|
    |<span data-ttu-id="be483-150">TextAlign</span><span class="sxs-lookup"><span data-stu-id="be483-150">TextAlign</span></span>|<xref:System.Drawing.ContentAlignment.MiddleLeft>|

5. <span data-ttu-id="be483-151">Powtórz krok 7 dla trzech <xref:System.Windows.Forms.ToolStripButton> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="be483-151">Repeat step 7 for three more <xref:System.Windows.Forms.ToolStripButton> controls.</span></span>

     <span data-ttu-id="be483-152">Nazwij kontrolki `calendarStackButton`, `contactsStackButton`, i `tasksStackButton`.</span><span class="sxs-lookup"><span data-stu-id="be483-152">Name the controls `calendarStackButton`, `contactsStackButton`, and `tasksStackButton`.</span></span> <span data-ttu-id="be483-153">Ustaw wartość <xref:System.Windows.Forms.Control.Text%2A> właściwości **kalendarza**, **kontakty**, i **zadania**, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="be483-153">Set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to **Calendar**, **Contacts**, and **Tasks**, respectively.</span></span>

## <a name="handle-events"></a><span data-ttu-id="be483-154">Obsługa zdarzeń</span><span class="sxs-lookup"><span data-stu-id="be483-154">Handle events</span></span>

<span data-ttu-id="be483-155">Dwa zdarzenia są ważne dla zapewnienia `StackView` kontroli działają poprawnie.</span><span class="sxs-lookup"><span data-stu-id="be483-155">Two events are important to make the `StackView` control behave correctly.</span></span> <span data-ttu-id="be483-156">Obsługa <xref:System.Windows.Forms.UserControl.Load> zdarzenie, aby poprawnie położenie formantu.</span><span class="sxs-lookup"><span data-stu-id="be483-156">Handle the <xref:System.Windows.Forms.UserControl.Load> event to position the control correctly.</span></span> <span data-ttu-id="be483-157">Obsługa <xref:System.Windows.Forms.ToolStripItem.Click> zdarzeń dla każdego <xref:System.Windows.Forms.ToolStripButton> zapewnienie `StackView` kontrolowania zachowania stanu podobny do <xref:System.Windows.Forms.RadioButton> kontroli.</span><span class="sxs-lookup"><span data-stu-id="be483-157">Handle the <xref:System.Windows.Forms.ToolStripItem.Click> event for each <xref:System.Windows.Forms.ToolStripButton> to give the `StackView` control state behavior similar to the <xref:System.Windows.Forms.RadioButton> control.</span></span>

1. <span data-ttu-id="be483-158">W programie Windows Forms Designer wybierz `StackView` kontroli.</span><span class="sxs-lookup"><span data-stu-id="be483-158">In the Windows Forms Designer, select the `StackView` control.</span></span>

2. <span data-ttu-id="be483-159">W **właściwości** okna, kliknij przycisk **zdarzenia**.</span><span class="sxs-lookup"><span data-stu-id="be483-159">In the **Properties** window, click **Events**.</span></span>

3. <span data-ttu-id="be483-160">Kliknij dwukrotnie zdarzenie obciążenia, aby wygenerować `StackView_Load` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="be483-160">Double-click the Load event to generate the `StackView_Load` event handler.</span></span>

4. <span data-ttu-id="be483-161">W `StackView_Load` procedura obsługi zdarzeń, skopiuj i wklej następujący kod.</span><span class="sxs-lookup"><span data-stu-id="be483-161">In the `StackView_Load` event handler, copy and paste the following code.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#3)]

5. <span data-ttu-id="be483-162">W programie Windows Forms Designer wybierz `mailStackButton` kontroli.</span><span class="sxs-lookup"><span data-stu-id="be483-162">In the Windows Forms Designer, select the `mailStackButton` control.</span></span>

6. <span data-ttu-id="be483-163">W **właściwości** okna, kliknij przycisk **zdarzenia**.</span><span class="sxs-lookup"><span data-stu-id="be483-163">In the **Properties** window, click **Events**.</span></span>

7. <span data-ttu-id="be483-164">Kliknij dwukrotnie zdarzenie Click.</span><span class="sxs-lookup"><span data-stu-id="be483-164">Double-click the Click event.</span></span>

     <span data-ttu-id="be483-165">Windows Forms Designer generuje `mailStackButton_Click` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="be483-165">The Windows Forms Designer generates the `mailStackButton_Click` event handler.</span></span>

8. <span data-ttu-id="be483-166">Zmień nazwę `mailStackButton_Click` procedurę obsługi zdarzeń do `stackButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="be483-166">Rename the `mailStackButton_Click` event handler to `stackButton_Click`.</span></span>

     <span data-ttu-id="be483-167">Aby uzyskać więcej informacji, zobacz [symbolu kodu Refaktoryzacja zmiany nazwy](/visualstudio/ide/reference/rename).</span><span class="sxs-lookup"><span data-stu-id="be483-167">For more information, see [Rename a code symbol refactoring](/visualstudio/ide/reference/rename).</span></span>

9. <span data-ttu-id="be483-168">Wstaw następujący kod do `stackButton_Click` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="be483-168">Insert the following code into the `stackButton_Click` event handler.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#4)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#4)]

10. <span data-ttu-id="be483-169">W programie Windows Forms Designer wybierz `calendarStackButton` kontroli.</span><span class="sxs-lookup"><span data-stu-id="be483-169">In the Windows Forms Designer, select the `calendarStackButton` control.</span></span>

11. <span data-ttu-id="be483-170">W **właściwości** oknie równa zdarzenie Click `stackButton_Click` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="be483-170">In the **Properties** window, set the Click event to the `stackButton_Click` event handler.</span></span>

12. <span data-ttu-id="be483-171">Powtórz kroki 10 i 11 dla `contactsStackButton` i `tasksStackButton` kontrolki.</span><span class="sxs-lookup"><span data-stu-id="be483-171">Repeat steps 10 and 11 for the `contactsStackButton` and `tasksStackButton` controls.</span></span>

## <a name="define-icons"></a><span data-ttu-id="be483-172">Zdefiniuj ikon</span><span class="sxs-lookup"><span data-stu-id="be483-172">Define icons</span></span>

<span data-ttu-id="be483-173">Każdy `StackView` przycisk ma skojarzona ikona.</span><span class="sxs-lookup"><span data-stu-id="be483-173">Each `StackView` button has an associated icon.</span></span> <span data-ttu-id="be483-174">Dla wygody, każda ikona jest reprezentowany jako ciąg zakodowany w formacie Base64, który jest przeprowadzona przed <xref:System.Drawing.Bitmap> utworzonych na jej podstawie.</span><span class="sxs-lookup"><span data-stu-id="be483-174">For convenience, each icon is represented as a Base64-encoded string, which is deserialized before a <xref:System.Drawing.Bitmap> is created from it.</span></span> <span data-ttu-id="be483-175">W środowisku produkcyjnym można przechowywać dane mapy bitowej jako zasób, a ikony są wyświetlane w programie Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="be483-175">In a production environment, you store bitmap data as a resource, and your icons appear in the Windows Forms Designer.</span></span> <span data-ttu-id="be483-176">Aby uzyskać więcej informacji, zobacz [jak: Dodawanie obrazów w tle do formularzy Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dff9f95f(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="be483-176">For more information, see [How to: Add Background Images to Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dff9f95f(v=vs.100)).</span></span>

1. <span data-ttu-id="be483-177">W edytorze kodu, Wstaw następujący kod do `StackView` definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="be483-177">In the Code Editor, insert the following code into the `StackView` class definition.</span></span> <span data-ttu-id="be483-178">Ten kod inicjalizuje bitmap do <xref:System.Windows.Forms.ToolStripButton> ikon.</span><span class="sxs-lookup"><span data-stu-id="be483-178">This code initializes the bitmaps for the <xref:System.Windows.Forms.ToolStripButton> icons.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#2)]

2. <span data-ttu-id="be483-179">Dodaj wywołanie do `InitializeImages` method in Class metoda `StackView` konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="be483-179">Add a call to the `InitializeImages` method in the `StackView` class constructor.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]

## <a name="implement-a-custom-renderer"></a><span data-ttu-id="be483-180">Implementowanie niestandardowego modułu renderowania</span><span class="sxs-lookup"><span data-stu-id="be483-180">Implement a custom renderer</span></span>

<span data-ttu-id="be483-181">Można dostosować większość elementów `StackView` kontrolować Moje Implementacja klasy, która pochodzi od klasy <xref:System.Windows.Forms.ToolStripRenderer> klasy.</span><span class="sxs-lookup"><span data-stu-id="be483-181">You can customize most elements of the `StackView` control my implementing a class that derives from the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span> <span data-ttu-id="be483-182">W tej procedurze, zostaną zaimplementowane <xref:System.Windows.Forms.ToolStripProfessionalRenderer> klasę, która dostosowuje uchwytu i rysuje gradientu tła <xref:System.Windows.Forms.ToolStripButton> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="be483-182">In this procedure, you will implement a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> class that customizes the grip and draws gradient backgrounds for the <xref:System.Windows.Forms.ToolStripButton> controls.</span></span>

1. <span data-ttu-id="be483-183">Wstaw następujący kod do `StackView` kontrolować definicji.</span><span class="sxs-lookup"><span data-stu-id="be483-183">Insert the following code into the `StackView` control definition.</span></span>

     <span data-ttu-id="be483-184">Jest to definicja `StackRenderer` klasy, co zastępuje <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, i <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> metody, aby utworzyć niestandardowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="be483-184">This is the definition for the `StackRenderer` class, which overrides the <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, and <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> methods to produce a custom appearance.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#10)]

2. <span data-ttu-id="be483-185">W `StackView` konstruktora kontrolki, Utwórz nowe wystąpienie klasy `StackRenderer` klasy, a następnie przypisz tego wystąpienia `stackStrip` kontrolki <xref:System.Windows.Forms.ToolStrip.Renderer%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="be483-185">In the `StackView` control's constructor, create a new instance of the `StackRenderer` class and assign this instance to the `stackStrip` control's <xref:System.Windows.Forms.ToolStrip.Renderer%2A> property.</span></span>

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]

## <a name="test-the-stackview-control"></a><span data-ttu-id="be483-186">Testowanie kontrolki StackView</span><span class="sxs-lookup"><span data-stu-id="be483-186">Test the StackView control</span></span>

<span data-ttu-id="be483-187">`StackView` Pochodzi od klasy formantu <xref:System.Windows.Forms.UserControl> klasy.</span><span class="sxs-lookup"><span data-stu-id="be483-187">The `StackView` control derives from the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="be483-188">W związku z tym, można przetestować kontrolki z **UserControl — kontener testu**.</span><span class="sxs-lookup"><span data-stu-id="be483-188">Therefore, you can test the control with the **UserControl Test Container**.</span></span> <span data-ttu-id="be483-189">Aby uzyskać więcej informacji, zobacz [jak: Testowanie zachowania UserControl w czasie wykonywania](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="be483-189">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

1. <span data-ttu-id="be483-190">Naciśnij klawisz **F5** Aby skompilować projekt i uruchomić **UserControl — kontener testowy**.</span><span class="sxs-lookup"><span data-stu-id="be483-190">Press **F5** to build the project and start the **UserControl Test Container**.</span></span>

2. <span data-ttu-id="be483-191">Przesuń wskaźnik nad przycisków `StackView` sterowania, a następnie kliknij przycisk, aby zobaczyć wygląd stanie wybrania.</span><span class="sxs-lookup"><span data-stu-id="be483-191">Move the pointer over the buttons of the `StackView` control, and then click a button to see the appearance of its selected state.</span></span>

## <a name="next-steps"></a><span data-ttu-id="be483-192">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="be483-192">Next steps</span></span>

<span data-ttu-id="be483-193">W tym instruktażu utworzono kontrolkę wielokrotnego niestandardowe klienta profesjonalny wygląd kontrolki Office XP.</span><span class="sxs-lookup"><span data-stu-id="be483-193">In this walkthrough, you have created a reusable custom client control with the professional appearance of an Office XP control.</span></span> <span data-ttu-id="be483-194">Możesz użyć <xref:System.Windows.Forms.ToolStrip> rodziny formantów do innych celów:</span><span class="sxs-lookup"><span data-stu-id="be483-194">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>

- <span data-ttu-id="be483-195">Tworzenie menu skrótów dla formantów z <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="be483-195">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="be483-196">Aby uzyskać więcej informacji, zobacz [— informacje o składniku ContextMenu](contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="be483-196">For more information, see [ContextMenu Component Overview](contextmenu-component-overview-windows-forms.md).</span></span>

- <span data-ttu-id="be483-197">Tworzenie formularza z automatycznie wypełnione standardowe menu.</span><span class="sxs-lookup"><span data-stu-id="be483-197">Create a form with an automatically populated standard menu.</span></span> <span data-ttu-id="be483-198">Aby uzyskać więcej informacji, zobacz [instruktażu: Zapewnianie elementów Menu standardowego dla formularza](walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="be483-198">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>

- <span data-ttu-id="be483-199">Tworzenie wielu formularza interfejsu (MDI) dokumentu z dokowanie <xref:System.Windows.Forms.ToolStrip> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="be483-199">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="be483-200">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie formularza MDI za pomocą scalania Menu i formantów ToolStrip](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="be483-200">For more information, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="be483-201">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="be483-201">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [<span data-ttu-id="be483-202">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="be483-202">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
- [<span data-ttu-id="be483-203">Instrukcje: Zapewnianie elementów Menu standardowego dla formularza</span><span class="sxs-lookup"><span data-stu-id="be483-203">How to: Provide Standard Menu Items to a Form</span></span>](how-to-provide-standard-menu-items-to-a-form.md)
