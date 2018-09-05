---
title: 'Wskazówki: tworzenie profesjonalnego formantu ToolStrip'
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
ms.openlocfilehash: 6435f33489be1355313e43a046b0e3169e1eaea3
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43538568"
---
# <a name="walkthrough-creating-a-professionally-styled-toolstrip-control"></a><span data-ttu-id="853cb-102">Wskazówki: tworzenie profesjonalnego formantu ToolStrip</span><span class="sxs-lookup"><span data-stu-id="853cb-102">Walkthrough: Creating a Professionally Styled ToolStrip Control</span></span>
<span data-ttu-id="853cb-103">Możesz nadać aplikacji <xref:System.Windows.Forms.ToolStrip> kontroluje profesjonalny wygląd i zachowanie, pisząc własne klasy pochodzącej od <xref:System.Windows.Forms.ToolStripProfessionalRenderer> typu.</span><span class="sxs-lookup"><span data-stu-id="853cb-103">You can give your application’s <xref:System.Windows.Forms.ToolStrip> controls a professional appearance and behavior by writing your own class derived from the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.</span></span>  
  
 <span data-ttu-id="853cb-104">W tym instruktażu przedstawiono sposób użycia <xref:System.Windows.Forms.ToolStrip> formantów, aby utworzyć formant złożony, który przypomina **okienka nawigacji** udostępniane przez Microsoft Outlook®.</span><span class="sxs-lookup"><span data-stu-id="853cb-104">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStrip> controls to create a composite control that resembles the **Navigation Pane** provided by Microsoft® Outlook®.</span></span> <span data-ttu-id="853cb-105">Następujące zadania są przedstawione w niniejszym przewodniku:</span><span class="sxs-lookup"><span data-stu-id="853cb-105">The following tasks are illustrated in this walkthrough:</span></span>  
  
-   <span data-ttu-id="853cb-106">Tworzenie projektu Biblioteka formantów Windows.</span><span class="sxs-lookup"><span data-stu-id="853cb-106">Creating a Windows Control Library project.</span></span>  
  
-   <span data-ttu-id="853cb-107">Projektowanie kontrolki StackView.</span><span class="sxs-lookup"><span data-stu-id="853cb-107">Designing the StackView Control.</span></span>  
  
-   <span data-ttu-id="853cb-108">Implementowanie niestandardowego modułu renderowania.</span><span class="sxs-lookup"><span data-stu-id="853cb-108">Implementing a Custom Renderer.</span></span>  
  
 <span data-ttu-id="853cb-109">Gdy skończysz, konieczne będzie formantu wielokrotnego niestandardowe klienta za pomocą profesjonalny wygląd kontrolki Microsoft Office® XP.</span><span class="sxs-lookup"><span data-stu-id="853cb-109">When you are finished, you will have a reusable custom client control with the professional appearance of a Microsoft Office® XP control.</span></span>  
  
 <span data-ttu-id="853cb-110">Aby skopiować kod, w tym temacie na jednej liście, zobacz [jak: tworzenie profesjonalnego różne formantu ToolStrip](../../../../docs/framework/winforms/controls/how-to-create-a-professionally-styled-toolstrip-control.md).</span><span class="sxs-lookup"><span data-stu-id="853cb-110">To copy the code in this topic as a single listing, see [How to: Create a Professionally Styled ToolStrip Control](../../../../docs/framework/winforms/controls/how-to-create-a-professionally-styled-toolstrip-control.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="853cb-111">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="853cb-111">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="853cb-112">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="853cb-112">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="853cb-113">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="853cb-113">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="853cb-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="853cb-114">Prerequisites</span></span>  
 <span data-ttu-id="853cb-115">Aby ukończyć ten przewodnik, potrzebne są:</span><span class="sxs-lookup"><span data-stu-id="853cb-115">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="853cb-116">Wystarczające uprawnienia, aby można było utworzyć i uruchomić projekty aplikacji Windows Forms na komputerze, w którym jest zainstalowany program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="853cb-116">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where Visual Studio is installed.</span></span>  
  
## <a name="creating-a-windows-control-library-project"></a><span data-ttu-id="853cb-117">Tworzenie projektu biblioteki kontrolek Windows</span><span class="sxs-lookup"><span data-stu-id="853cb-117">Creating a Windows Control Library Project</span></span>  
 <span data-ttu-id="853cb-118">Pierwszym krokiem jest, aby utworzyć projekt Biblioteka formantów.</span><span class="sxs-lookup"><span data-stu-id="853cb-118">The first step is to create the control library project.</span></span>  
  
#### <a name="to-create-the-control-library-project"></a><span data-ttu-id="853cb-119">Aby utworzyć projekt Biblioteka formantów</span><span class="sxs-lookup"><span data-stu-id="853cb-119">To create the control library project</span></span>  
  
1.  <span data-ttu-id="853cb-120">Utwórz nowy projekt Biblioteka formantów Windows o nazwie `StackViewLibrary`.</span><span class="sxs-lookup"><span data-stu-id="853cb-120">Create a new Windows Control Library project named `StackViewLibrary`.</span></span>  
  
2.  <span data-ttu-id="853cb-121">W **Eksploratora rozwiązań**, usunąć projekt domyślny formant przez usunięcie pliku źródłowego o nazwie "UserControl1.cs" lub "UserControl1.vb", w zależności od tego, w wybranym języku.</span><span class="sxs-lookup"><span data-stu-id="853cb-121">In **Solution Explorer**, delete the project's default control by deleting the source file named "UserControl1.cs" or "UserControl1.vb", depending on your language of choice.</span></span>  
  
     <span data-ttu-id="853cb-122">Aby uzyskać więcej informacji, zobacz [NIB: instrukcje: usuwanie, usuwania i wykluczyć elementy](https://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span><span class="sxs-lookup"><span data-stu-id="853cb-122">For more information, see [NIB:How to: Remove, Delete, and Exclude Items](https://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span></span>  
  
3.  <span data-ttu-id="853cb-123">Dodaj nową <xref:System.Windows.Forms.UserControl> elementu do **StackViewLibrary** projektu.</span><span class="sxs-lookup"><span data-stu-id="853cb-123">Add a new <xref:System.Windows.Forms.UserControl> item to the **StackViewLibrary** project.</span></span> <span data-ttu-id="853cb-124">Nazwij nowy plik źródłowy podstawowej z `StackView`.</span><span class="sxs-lookup"><span data-stu-id="853cb-124">Give the new source file a base name of `StackView`.</span></span>  
  
## <a name="designing-the-stackview-control"></a><span data-ttu-id="853cb-125">Projektowanie kontrolki StackView</span><span class="sxs-lookup"><span data-stu-id="853cb-125">Designing the StackView Control</span></span>  
 <span data-ttu-id="853cb-126">`StackView` Kontrolka jest kontrolką złożoną z jeden element podrzędny <xref:System.Windows.Forms.ToolStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="853cb-126">The `StackView` control is a composite control with one child <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="853cb-127">Aby uzyskać więcej informacji na temat formanty złożone zobacz [różne typy kontrolek niestandardowych](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="853cb-127">For more information about composite controls, see [Varieties of Custom Controls](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).</span></span>  
  
#### <a name="to-design-the-stackview-control"></a><span data-ttu-id="853cb-128">Aby zaprojektować kontroli StackView</span><span class="sxs-lookup"><span data-stu-id="853cb-128">To design the StackView control</span></span>  
  
1.  <span data-ttu-id="853cb-129">Z **przybornika**, przeciągnij <xref:System.Windows.Forms.ToolStrip> kontrolki na powierzchnię projektową.</span><span class="sxs-lookup"><span data-stu-id="853cb-129">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStrip> control to the design surface.</span></span>  
  
2.  <span data-ttu-id="853cb-130">W **właściwości** oknie <xref:System.Windows.Forms.ToolStrip> właściwości formantu, zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="853cb-130">In the **Properties** window, set the <xref:System.Windows.Forms.ToolStrip> control's properties according to the following table.</span></span>  
  
    |<span data-ttu-id="853cb-131">Właściwość</span><span class="sxs-lookup"><span data-stu-id="853cb-131">Property</span></span>|<span data-ttu-id="853cb-132">Wartość</span><span class="sxs-lookup"><span data-stu-id="853cb-132">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="853cb-133">Nazwa</span><span class="sxs-lookup"><span data-stu-id="853cb-133">Name</span></span>|`stackStrip`|  
    |<span data-ttu-id="853cb-134">CanOverflow</span><span class="sxs-lookup"><span data-stu-id="853cb-134">CanOverflow</span></span>|`false`|  
    |<span data-ttu-id="853cb-135">Dock</span><span class="sxs-lookup"><span data-stu-id="853cb-135">Dock</span></span>|<xref:System.Windows.Forms.DockStyle.Bottom>|  
    |<span data-ttu-id="853cb-136">Czcionka</span><span class="sxs-lookup"><span data-stu-id="853cb-136">Font</span></span>|`Tahoma, 10pt, style=Bold`|  
    |<span data-ttu-id="853cb-137">GripStyle</span><span class="sxs-lookup"><span data-stu-id="853cb-137">GripStyle</span></span>|<xref:System.Windows.Forms.ToolStripGripStyle.Hidden>|  
    |<span data-ttu-id="853cb-138">LayoutStyle</span><span class="sxs-lookup"><span data-stu-id="853cb-138">LayoutStyle</span></span>|<xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>|  
    |<span data-ttu-id="853cb-139">Dopełnienie</span><span class="sxs-lookup"><span data-stu-id="853cb-139">Padding</span></span>|`0, 7, 0, 0`|  
    |<span data-ttu-id="853cb-140">RenderMode</span><span class="sxs-lookup"><span data-stu-id="853cb-140">RenderMode</span></span>|<xref:System.Windows.Forms.ToolStripRenderMode.Professional>|  
  
3.  <span data-ttu-id="853cb-141">W programie Windows Forms Designer kliknij <xref:System.Windows.Forms.ToolStrip> kontrolki **Dodaj** przycisku i Dodaj <xref:System.Windows.Forms.ToolStripButton> do `stackStrip` kontroli.</span><span class="sxs-lookup"><span data-stu-id="853cb-141">In the Windows Forms Designer, click the <xref:System.Windows.Forms.ToolStrip> control's **Add** button and add a <xref:System.Windows.Forms.ToolStripButton> to the `stackStrip` control.</span></span>  
  
4.  <span data-ttu-id="853cb-142">W **właściwości** oknie <xref:System.Windows.Forms.ToolStripButton> właściwości formantu, zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="853cb-142">In the **Properties** window, set the <xref:System.Windows.Forms.ToolStripButton> control's properties according to the following table.</span></span>  
  
    |<span data-ttu-id="853cb-143">Właściwość</span><span class="sxs-lookup"><span data-stu-id="853cb-143">Property</span></span>|<span data-ttu-id="853cb-144">Wartość</span><span class="sxs-lookup"><span data-stu-id="853cb-144">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="853cb-145">Nazwa</span><span class="sxs-lookup"><span data-stu-id="853cb-145">Name</span></span>|`mailStackButton`|  
    |<span data-ttu-id="853cb-146">CheckOnClick</span><span class="sxs-lookup"><span data-stu-id="853cb-146">CheckOnClick</span></span>|<span data-ttu-id="853cb-147">true</span><span class="sxs-lookup"><span data-stu-id="853cb-147">true</span></span>|  
    |<span data-ttu-id="853cb-148">Wartość CheckState</span><span class="sxs-lookup"><span data-stu-id="853cb-148">CheckState</span></span>|<xref:System.Windows.Forms.CheckState.Checked>|  
    |<span data-ttu-id="853cb-149">DisplayStyle</span><span class="sxs-lookup"><span data-stu-id="853cb-149">DisplayStyle</span></span>|<xref:System.Windows.Forms.ToolStripItemDisplayStyle.ImageAndText>|  
    |<span data-ttu-id="853cb-150">ImageAlign</span><span class="sxs-lookup"><span data-stu-id="853cb-150">ImageAlign</span></span>|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
    |<span data-ttu-id="853cb-151">ImageScaling</span><span class="sxs-lookup"><span data-stu-id="853cb-151">ImageScaling</span></span>|<xref:System.Windows.Forms.ToolStripItemImageScaling.None>|  
    |<span data-ttu-id="853cb-152">ImageTransparentColor</span><span class="sxs-lookup"><span data-stu-id="853cb-152">ImageTransparentColor</span></span>|`238, 238, 238`|  
    |<span data-ttu-id="853cb-153">Margines</span><span class="sxs-lookup"><span data-stu-id="853cb-153">Margin</span></span>|`0, 0, 0, 0`|  
    |<span data-ttu-id="853cb-154">Dopełnienie</span><span class="sxs-lookup"><span data-stu-id="853cb-154">Padding</span></span>|`3, 3, 3, 3`|  
    |<span data-ttu-id="853cb-155">Tekst</span><span class="sxs-lookup"><span data-stu-id="853cb-155">Text</span></span>|<span data-ttu-id="853cb-156">**wiadomości e-mail**</span><span class="sxs-lookup"><span data-stu-id="853cb-156">**Mail**</span></span>|  
    |<span data-ttu-id="853cb-157">TextAlign</span><span class="sxs-lookup"><span data-stu-id="853cb-157">TextAlign</span></span>|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
  
5.  <span data-ttu-id="853cb-158">Powtórz krok 7 dla trzech <xref:System.Windows.Forms.ToolStripButton> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="853cb-158">Repeat step 7 for three more <xref:System.Windows.Forms.ToolStripButton> controls.</span></span>  
  
     <span data-ttu-id="853cb-159">Nazwij kontrolki `calendarStackButton`, `contactsStackButton`, i `tasksStackButton`.</span><span class="sxs-lookup"><span data-stu-id="853cb-159">Name the controls `calendarStackButton`, `contactsStackButton`, and `tasksStackButton`.</span></span> <span data-ttu-id="853cb-160">Ustaw wartość <xref:System.Windows.Forms.Control.Text%2A> właściwości **kalendarza**, **kontakty**, i **zadania**, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="853cb-160">Set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to **Calendar**, **Contacts**, and **Tasks**, respectively.</span></span>  
  
## <a name="handling-events"></a><span data-ttu-id="853cb-161">Obsługa zdarzeń</span><span class="sxs-lookup"><span data-stu-id="853cb-161">Handling Events</span></span>  
 <span data-ttu-id="853cb-162">Dwa zdarzenia są ważne dla zapewnienia `StackView` kontroli działają poprawnie.</span><span class="sxs-lookup"><span data-stu-id="853cb-162">Two events are important to make the `StackView` control behave correctly.</span></span> <span data-ttu-id="853cb-163">Obsługa <xref:System.Windows.Forms.UserControl.Load> zdarzenie, aby poprawnie położenie formantu.</span><span class="sxs-lookup"><span data-stu-id="853cb-163">Handle the <xref:System.Windows.Forms.UserControl.Load> event to position the control correctly.</span></span> <span data-ttu-id="853cb-164">Obsługa <xref:System.Windows.Forms.ToolStripItem.Click> zdarzeń dla każdego <xref:System.Windows.Forms.ToolStripButton> zapewnienie `StackView` kontrolowania zachowania stanu podobny do <xref:System.Windows.Forms.RadioButton> kontroli.</span><span class="sxs-lookup"><span data-stu-id="853cb-164">Handle the <xref:System.Windows.Forms.ToolStripItem.Click> event for each <xref:System.Windows.Forms.ToolStripButton> to give the `StackView` control state behavior similar to the <xref:System.Windows.Forms.RadioButton> control.</span></span>  
  
#### <a name="to-handle-events"></a><span data-ttu-id="853cb-165">Do obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="853cb-165">To handle events</span></span>  
  
1.  <span data-ttu-id="853cb-166">W programie Windows Forms Designer wybierz `StackView` kontroli.</span><span class="sxs-lookup"><span data-stu-id="853cb-166">In the Windows Forms Designer, select the `StackView` control.</span></span>  
  
2.  <span data-ttu-id="853cb-167">W **właściwości** okna, kliknij przycisk **zdarzenia**.</span><span class="sxs-lookup"><span data-stu-id="853cb-167">In the **Properties** window, click **Events**.</span></span>  
  
3.  <span data-ttu-id="853cb-168">Kliknij dwukrotnie zdarzenie obciążenia, aby wygenerować `StackView_Load` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="853cb-168">Double-click the Load event to generate the `StackView_Load` event handler.</span></span>  
  
4.  <span data-ttu-id="853cb-169">W `StackView_Load` procedura obsługi zdarzeń, skopiuj i wklej następujący kod.</span><span class="sxs-lookup"><span data-stu-id="853cb-169">In the `StackView_Load` event handler, copy and paste the following code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#3)]  
  
5.  <span data-ttu-id="853cb-170">W programie Windows Forms Designer wybierz `mailStackButton` kontroli.</span><span class="sxs-lookup"><span data-stu-id="853cb-170">In the Windows Forms Designer, select the `mailStackButton` control.</span></span>  
  
6.  <span data-ttu-id="853cb-171">W **właściwości** okna, kliknij przycisk **zdarzenia**.</span><span class="sxs-lookup"><span data-stu-id="853cb-171">In the **Properties** window, click **Events**.</span></span>  
  
7.  <span data-ttu-id="853cb-172">Kliknij dwukrotnie zdarzenie Click.</span><span class="sxs-lookup"><span data-stu-id="853cb-172">Double-click the Click event.</span></span>  
  
     <span data-ttu-id="853cb-173">Windows Forms Designer generuje `mailStackButton_Click` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="853cb-173">The Windows Forms Designer generates the `mailStackButton_Click` event handler.</span></span>  
  
8.  <span data-ttu-id="853cb-174">Zmień nazwę `mailStackButton_Click` procedurę obsługi zdarzeń do `stackButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="853cb-174">Rename the `mailStackButton_Click` event handler to `stackButton_Click`.</span></span>  
  
     <span data-ttu-id="853cb-175">Aby uzyskać więcej informacji, zobacz [porady: zmiana nazwy identyfikatora (Visual Basic)](https://msdn.microsoft.com/library/e5a5edf8-3dba-4119-81f4-fc2aba180e0c).</span><span class="sxs-lookup"><span data-stu-id="853cb-175">For more information, see [How to: Rename an Identifier (Visual Basic)](https://msdn.microsoft.com/library/e5a5edf8-3dba-4119-81f4-fc2aba180e0c).</span></span>  
  
9. <span data-ttu-id="853cb-176">Wstaw następujący kod do `stackButton_Click` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="853cb-176">Insert the following code into the `stackButton_Click` event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#4)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#4)]  
  
10. <span data-ttu-id="853cb-177">W programie Windows Forms Designer wybierz `calendarStackButton` kontroli.</span><span class="sxs-lookup"><span data-stu-id="853cb-177">In the Windows Forms Designer, select the `calendarStackButton` control.</span></span>  
  
11. <span data-ttu-id="853cb-178">W **właściwości** oknie równa zdarzenie Click `stackButton_Click` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="853cb-178">In the **Properties** window, set the Click event to the `stackButton_Click` event handler.</span></span>  
  
12. <span data-ttu-id="853cb-179">Powtórz kroki 10 i 11 dla `contactsStackButton` i `tasksStackButton` kontrolki.</span><span class="sxs-lookup"><span data-stu-id="853cb-179">Repeat steps 10 and 11 for the `contactsStackButton` and `tasksStackButton` controls.</span></span>  
  
## <a name="defining-icons"></a><span data-ttu-id="853cb-180">Definiowanie ikon</span><span class="sxs-lookup"><span data-stu-id="853cb-180">Defining Icons</span></span>  
 <span data-ttu-id="853cb-181">Każdy `StackView` przycisk ma skojarzona ikona.</span><span class="sxs-lookup"><span data-stu-id="853cb-181">Each `StackView` button has an associated icon.</span></span> <span data-ttu-id="853cb-182">Dla wygody, każda ikona jest reprezentowany jako ciąg zakodowany w formacie Base64, który jest przeprowadzona przed <xref:System.Drawing.Bitmap> utworzonych na jej podstawie.</span><span class="sxs-lookup"><span data-stu-id="853cb-182">For convenience, each icon is represented as a Base64-encoded string, which is deserialized before a <xref:System.Drawing.Bitmap> is created from it.</span></span> <span data-ttu-id="853cb-183">W środowisku produkcyjnym można przechowywać dane mapy bitowej jako zasób, a ikony są wyświetlane w programie Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="853cb-183">In a production environment, you store bitmap data as a resource, and your icons appear in the Windows Forms Designer.</span></span> <span data-ttu-id="853cb-184">Aby uzyskać więcej informacji, zobacz [porady: Dodawanie obrazów tła do formularzy Windows Forms](https://msdn.microsoft.com/library/7a509ba2-055c-4ae6-b88a-54625c6d9aff).</span><span class="sxs-lookup"><span data-stu-id="853cb-184">For more information, see [How to: Add Background Images to Windows Forms](https://msdn.microsoft.com/library/7a509ba2-055c-4ae6-b88a-54625c6d9aff).</span></span>  
  
#### <a name="to-define-icons"></a><span data-ttu-id="853cb-185">Aby zdefiniować ikon</span><span class="sxs-lookup"><span data-stu-id="853cb-185">To define icons</span></span>  
  
1.  <span data-ttu-id="853cb-186">W edytorze kodu, Wstaw następujący kod do `StackView` definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="853cb-186">In the Code Editor, insert the following code into the `StackView` class definition.</span></span> <span data-ttu-id="853cb-187">Ten kod inicjalizuje bitmap do <xref:System.Windows.Forms.ToolStripButton> ikon.</span><span class="sxs-lookup"><span data-stu-id="853cb-187">This code initializes the bitmaps for the <xref:System.Windows.Forms.ToolStripButton> icons.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#2)]  
  
2.  <span data-ttu-id="853cb-188">Dodaj wywołanie do `InitializeImages` method in Class metoda `StackView` konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="853cb-188">Add a call to the `InitializeImages` method in the `StackView` class constructor.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="implementing-a-custom-renderer"></a><span data-ttu-id="853cb-189">Implementowanie niestandardowego modułu renderowania</span><span class="sxs-lookup"><span data-stu-id="853cb-189">Implementing a Custom Renderer</span></span>  
 <span data-ttu-id="853cb-190">Można dostosować większość elementów `StackView` kontrolować Moje Implementacja klasy, która pochodzi od klasy <xref:System.Windows.Forms.ToolStripRenderer> klasy.</span><span class="sxs-lookup"><span data-stu-id="853cb-190">You can customize most elements of the `StackView` control my implementing a class that derives from the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span> <span data-ttu-id="853cb-191">W tej procedurze, zostaną zaimplementowane <xref:System.Windows.Forms.ToolStripProfessionalRenderer> klasę, która dostosowuje uchwytu i rysuje gradientu tła <xref:System.Windows.Forms.ToolStripButton> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="853cb-191">In this procedure, you will implement a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> class that customizes the grip and draws gradient backgrounds for the <xref:System.Windows.Forms.ToolStripButton> controls.</span></span>  
  
#### <a name="to-implement-a-custom-renderer"></a><span data-ttu-id="853cb-192">Aby zaimplementować niestandardowego modułu renderowania</span><span class="sxs-lookup"><span data-stu-id="853cb-192">To implement a custom renderer</span></span>  
  
1.  <span data-ttu-id="853cb-193">Wstaw następujący kod do `StackView` kontrolować definicji.</span><span class="sxs-lookup"><span data-stu-id="853cb-193">Insert the following code into the `StackView` control definition.</span></span>  
  
     <span data-ttu-id="853cb-194">Jest to definicja `StackRenderer` klasy, co zastępuje <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, i <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> metody, aby utworzyć niestandardowy wygląd.</span><span class="sxs-lookup"><span data-stu-id="853cb-194">This is the definition for the `StackRenderer` class, which overrides the <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, and <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> methods to produce a custom appearance.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#10)]  
  
2.  <span data-ttu-id="853cb-195">W `StackView` konstruktora kontrolki, Utwórz nowe wystąpienie klasy `StackRenderer` klasy, a następnie przypisz tego wystąpienia `stackStrip` kontrolki <xref:System.Windows.Forms.ToolStrip.Renderer%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="853cb-195">In the `StackView` control's constructor, create a new instance of the `StackRenderer` class and assign this instance to the `stackStrip` control's <xref:System.Windows.Forms.ToolStrip.Renderer%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="testing-the-stackview-control"></a><span data-ttu-id="853cb-196">Testowanie kontrolki StackView</span><span class="sxs-lookup"><span data-stu-id="853cb-196">Testing the StackView Control</span></span>  
 <span data-ttu-id="853cb-197">`StackView` Pochodzi od klasy formantu <xref:System.Windows.Forms.UserControl> klasy.</span><span class="sxs-lookup"><span data-stu-id="853cb-197">The `StackView` control derives from the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="853cb-198">W związku z tym, można przetestować kontrolki z **UserControl — kontener testu**.</span><span class="sxs-lookup"><span data-stu-id="853cb-198">Therefore, you can test the control with the **UserControl Test Container**.</span></span> <span data-ttu-id="853cb-199">Aby uzyskać więcej informacji, zobacz [porady: testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="853cb-199">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
#### <a name="to-test-the-stackview-control"></a><span data-ttu-id="853cb-200">Aby przetestować formant StackView</span><span class="sxs-lookup"><span data-stu-id="853cb-200">To test the StackView control</span></span>  
  
1.  <span data-ttu-id="853cb-201">Naciśnij klawisz F5, aby skompilować projekt i uruchomić **UserControl — kontener testowy**.</span><span class="sxs-lookup"><span data-stu-id="853cb-201">Press F5 to build the project and start the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="853cb-202">Przesuń wskaźnik nad przycisków `StackView` sterowania, a następnie kliknij przycisk, aby zobaczyć wygląd stanie wybrania.</span><span class="sxs-lookup"><span data-stu-id="853cb-202">Move the pointer over the buttons of the `StackView` control, and then click a button to see the appearance of its selected state.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="853cb-203">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="853cb-203">Next Steps</span></span>  
 <span data-ttu-id="853cb-204">W tym instruktażu utworzono kontrolkę wielokrotnego niestandardowe klienta profesjonalny wygląd kontrolki Office XP.</span><span class="sxs-lookup"><span data-stu-id="853cb-204">In this walkthrough, you have created a reusable custom client control with the professional appearance of an Office XP control.</span></span> <span data-ttu-id="853cb-205">Możesz użyć <xref:System.Windows.Forms.ToolStrip> rodziny formantów do innych celów:</span><span class="sxs-lookup"><span data-stu-id="853cb-205">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>  
  
-   <span data-ttu-id="853cb-206">Tworzenie menu skrótów dla formantów z <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="853cb-206">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="853cb-207">Aby uzyskać więcej informacji, zobacz [— informacje o składniku ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="853cb-207">For more information, see [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="853cb-208">Tworzenie formularza z automatycznie wypełnione standardowe menu.</span><span class="sxs-lookup"><span data-stu-id="853cb-208">Create a form with an automatically populated standard menu.</span></span> <span data-ttu-id="853cb-209">Aby uzyskać więcej informacji, zobacz [wskazówki: zapewnianie standardowych elementów Menu do formularza](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="853cb-209">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>  
  
-   <span data-ttu-id="853cb-210">Tworzenie wielu formularza interfejsu (MDI) dokumentu z dokowanie <xref:System.Windows.Forms.ToolStrip> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="853cb-210">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="853cb-211">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie formularza MDI za pomocą scalania Menu i formantów ToolStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="853cb-211">For more information, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="853cb-212">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="853cb-212">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="853cb-213">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="853cb-213">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [<span data-ttu-id="853cb-214">Instrukcje: zapewnianie elementów menu standardowego dla formularza</span><span class="sxs-lookup"><span data-stu-id="853cb-214">How to: Provide Standard Menu Items to a Form</span></span>](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)
