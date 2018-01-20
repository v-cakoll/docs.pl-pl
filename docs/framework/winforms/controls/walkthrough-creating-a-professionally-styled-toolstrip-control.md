---
title: "Wskazówki: tworzenie profesjonalnego formantu ToolStrip"
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
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- toolbars [Windows Forms], walkthroughs
- ToolStrip control [Windows Forms], creating professionally styled controls
ms.assetid: b52339ae-f1d3-494e-996e-eb455614098a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ab9adb72a174da25298b6ea104b002914de0cc40
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-creating-a-professionally-styled-toolstrip-control"></a><span data-ttu-id="b5770-102">Wskazówki: tworzenie profesjonalnego formantu ToolStrip</span><span class="sxs-lookup"><span data-stu-id="b5770-102">Walkthrough: Creating a Professionally Styled ToolStrip Control</span></span>
<span data-ttu-id="b5770-103">Umożliwia aplikacji <xref:System.Windows.Forms.ToolStrip> określa profesjonalny wygląd i zachowanie, tworząc własne klasy pochodzące z <xref:System.Windows.Forms.ToolStripProfessionalRenderer> typu.</span><span class="sxs-lookup"><span data-stu-id="b5770-103">You can give your application’s <xref:System.Windows.Forms.ToolStrip> controls a professional appearance and behavior by writing your own class derived from the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.</span></span>  
  
 <span data-ttu-id="b5770-104">W tym przewodniku przedstawiono sposób użycia <xref:System.Windows.Forms.ToolStrip> służy do tworzenia złożonych kontrolek, podobny **okienka nawigacji** udostępniane przez Microsoft Outlook®.</span><span class="sxs-lookup"><span data-stu-id="b5770-104">This walkthrough demonstrates how to use <xref:System.Windows.Forms.ToolStrip> controls to create a composite control that resembles the **Navigation Pane** provided by Microsoft® Outlook®.</span></span> <span data-ttu-id="b5770-105">Następujące zadania są przedstawione w tym przewodniku:</span><span class="sxs-lookup"><span data-stu-id="b5770-105">The following tasks are illustrated in this walkthrough:</span></span>  
  
-   <span data-ttu-id="b5770-106">Tworzenie projektu Biblioteka formantów systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b5770-106">Creating a Windows Control Library project.</span></span>  
  
-   <span data-ttu-id="b5770-107">Projektowania formantu StackView.</span><span class="sxs-lookup"><span data-stu-id="b5770-107">Designing the StackView Control.</span></span>  
  
-   <span data-ttu-id="b5770-108">Implementowanie niestandardowego modułu renderowania.</span><span class="sxs-lookup"><span data-stu-id="b5770-108">Implementing a Custom Renderer.</span></span>  
  
 <span data-ttu-id="b5770-109">Gdy skończysz, konieczne będzie formantu do ponownego użycia niestandardowego klienta o profesjonalny wygląd formantu Microsoft Office® XP.</span><span class="sxs-lookup"><span data-stu-id="b5770-109">When you are finished, you will have a reusable custom client control with the professional appearance of a Microsoft Office® XP control.</span></span>  
  
 <span data-ttu-id="b5770-110">Aby skopiować kod w tym temacie na jednej liście, zobacz [porady: tworzenie profesjonalnego styl formantu ToolStrip](../../../../docs/framework/winforms/controls/how-to-create-a-professionally-styled-toolstrip-control.md).</span><span class="sxs-lookup"><span data-stu-id="b5770-110">To copy the code in this topic as a single listing, see [How to: Create a Professionally Styled ToolStrip Control](../../../../docs/framework/winforms/controls/how-to-create-a-professionally-styled-toolstrip-control.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5770-111">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="b5770-111">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b5770-112">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="b5770-112">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b5770-113">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="b5770-113">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b5770-114">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="b5770-114">Prerequisites</span></span>  
 <span data-ttu-id="b5770-115">W celu przeprowadzenia tego instruktażu potrzebne są:</span><span class="sxs-lookup"><span data-stu-id="b5770-115">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="b5770-116">Wystarczających uprawnień, aby można było utworzyć i uruchomić projektów aplikacji formularzy systemu Windows na komputerze, którym [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="b5770-116">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] is installed.</span></span>  
  
## <a name="creating-a-windows-control-library-project"></a><span data-ttu-id="b5770-117">Tworzenie projektu biblioteki sterowania systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b5770-117">Creating a Windows Control Library Project</span></span>  
 <span data-ttu-id="b5770-118">Pierwszym krokiem jest do tworzenia projektu biblioteki formantu.</span><span class="sxs-lookup"><span data-stu-id="b5770-118">The first step is to create the control library project.</span></span>  
  
#### <a name="to-create-the-control-library-project"></a><span data-ttu-id="b5770-119">Aby utworzyć projekt z kontroli biblioteki</span><span class="sxs-lookup"><span data-stu-id="b5770-119">To create the control library project</span></span>  
  
1.  <span data-ttu-id="b5770-120">Utwórz nowy projekt Biblioteka formantów systemu Windows o nazwie `StackViewLibrary`.</span><span class="sxs-lookup"><span data-stu-id="b5770-120">Create a new Windows Control Library project named `StackViewLibrary`.</span></span>  
  
2.  <span data-ttu-id="b5770-121">W **Eksploratora rozwiązań**, usuń formant domyślnego projektu przez usunięcie pliku źródłowego o nazwie "UserControl1.cs" lub "UserControl1.vb", w zależności od języka wybór.</span><span class="sxs-lookup"><span data-stu-id="b5770-121">In **Solution Explorer**, delete the project's default control by deleting the source file named "UserControl1.cs" or "UserControl1.vb", depending on your language of choice.</span></span>  
  
     <span data-ttu-id="b5770-122">Aby uzyskać więcej informacji, zobacz [NIB: porady: usuwanie, usuwania i wykluczanie elementów](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span><span class="sxs-lookup"><span data-stu-id="b5770-122">For more information, see [NIB:How to: Remove, Delete, and Exclude Items](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).</span></span>  
  
3.  <span data-ttu-id="b5770-123">Dodaj nową <xref:System.Windows.Forms.UserControl> elementu do **StackViewLibrary** projektu.</span><span class="sxs-lookup"><span data-stu-id="b5770-123">Add a new <xref:System.Windows.Forms.UserControl> item to the **StackViewLibrary** project.</span></span> <span data-ttu-id="b5770-124">Nadaj nazwę podstawową nowy plik źródłowy `StackView`.</span><span class="sxs-lookup"><span data-stu-id="b5770-124">Give the new source file a base name of `StackView`.</span></span>  
  
## <a name="designing-the-stackview-control"></a><span data-ttu-id="b5770-125">Projektowania formantu StackView</span><span class="sxs-lookup"><span data-stu-id="b5770-125">Designing the StackView Control</span></span>  
 <span data-ttu-id="b5770-126">`StackView` Formant jest formantu złożonego za pomocą jeden element podrzędny <xref:System.Windows.Forms.ToolStrip> formantu.</span><span class="sxs-lookup"><span data-stu-id="b5770-126">The `StackView` control is a composite control with one child <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="b5770-127">Aby uzyskać więcej informacji na temat formanty złożone, zobacz [odmian Kontrolki niestandardowe](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="b5770-127">For more information about composite controls, see [Varieties of Custom Controls](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).</span></span>  
  
#### <a name="to-design-the-stackview-control"></a><span data-ttu-id="b5770-128">Projekt kontroli StackView</span><span class="sxs-lookup"><span data-stu-id="b5770-128">To design the StackView control</span></span>  
  
1.  <span data-ttu-id="b5770-129">Z **przybornika**, przeciągnij <xref:System.Windows.Forms.ToolStrip> sterowania na powierzchnię projektu.</span><span class="sxs-lookup"><span data-stu-id="b5770-129">From the **Toolbox**, drag a <xref:System.Windows.Forms.ToolStrip> control to the design surface.</span></span>  
  
2.  <span data-ttu-id="b5770-130">W **właściwości** ustaw <xref:System.Windows.Forms.ToolStrip> właściwości formantu zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="b5770-130">In the **Properties** window, set the <xref:System.Windows.Forms.ToolStrip> control's properties according to the following table.</span></span>  
  
    |<span data-ttu-id="b5770-131">Właściwość</span><span class="sxs-lookup"><span data-stu-id="b5770-131">Property</span></span>|<span data-ttu-id="b5770-132">Wartość</span><span class="sxs-lookup"><span data-stu-id="b5770-132">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="b5770-133">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b5770-133">Name</span></span>|`stackStrip`|  
    |<span data-ttu-id="b5770-134">CanOverflow</span><span class="sxs-lookup"><span data-stu-id="b5770-134">CanOverflow</span></span>|`false`|  
    |<span data-ttu-id="b5770-135">Doku.</span><span class="sxs-lookup"><span data-stu-id="b5770-135">Dock</span></span>|<xref:System.Windows.Forms.DockStyle.Bottom>|  
    |<span data-ttu-id="b5770-136">Czcionki</span><span class="sxs-lookup"><span data-stu-id="b5770-136">Font</span></span>|`Tahoma, 10pt, style=Bold`|  
    |<span data-ttu-id="b5770-137">GripStyle</span><span class="sxs-lookup"><span data-stu-id="b5770-137">GripStyle</span></span>|<xref:System.Windows.Forms.ToolStripGripStyle.Hidden>|  
    |<span data-ttu-id="b5770-138">LayoutStyle</span><span class="sxs-lookup"><span data-stu-id="b5770-138">LayoutStyle</span></span>|<xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>|  
    |<span data-ttu-id="b5770-139">Dopełnienie</span><span class="sxs-lookup"><span data-stu-id="b5770-139">Padding</span></span>|`0, 7, 0, 0`|  
    |<span data-ttu-id="b5770-140">RenderMode</span><span class="sxs-lookup"><span data-stu-id="b5770-140">RenderMode</span></span>|<xref:System.Windows.Forms.ToolStripRenderMode.Professional>|  
  
3.  <span data-ttu-id="b5770-141">W narzędziu Projektant dla formularzy systemu Windows, kliknij przycisk <xref:System.Windows.Forms.ToolStrip> formantu **Dodaj** przycisk i dodać <xref:System.Windows.Forms.ToolStripButton> do `stackStrip` formantu.</span><span class="sxs-lookup"><span data-stu-id="b5770-141">In the Windows Forms Designer, click the <xref:System.Windows.Forms.ToolStrip> control's **Add** button and add a <xref:System.Windows.Forms.ToolStripButton> to the `stackStrip` control.</span></span>  
  
4.  <span data-ttu-id="b5770-142">W **właściwości** ustaw <xref:System.Windows.Forms.ToolStripButton> właściwości formantu zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="b5770-142">In the **Properties** window, set the <xref:System.Windows.Forms.ToolStripButton> control's properties according to the following table.</span></span>  
  
    |<span data-ttu-id="b5770-143">Właściwość</span><span class="sxs-lookup"><span data-stu-id="b5770-143">Property</span></span>|<span data-ttu-id="b5770-144">Wartość</span><span class="sxs-lookup"><span data-stu-id="b5770-144">Value</span></span>|  
    |--------------|-----------|  
    |<span data-ttu-id="b5770-145">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b5770-145">Name</span></span>|`mailStackButton`|  
    |<span data-ttu-id="b5770-146">CheckOnClick</span><span class="sxs-lookup"><span data-stu-id="b5770-146">CheckOnClick</span></span>|<span data-ttu-id="b5770-147">true</span><span class="sxs-lookup"><span data-stu-id="b5770-147">true</span></span>|  
    |<span data-ttu-id="b5770-148">CheckState</span><span class="sxs-lookup"><span data-stu-id="b5770-148">CheckState</span></span>|<xref:System.Windows.Forms.CheckState.Checked>|  
    |<span data-ttu-id="b5770-149">DisplayStyle</span><span class="sxs-lookup"><span data-stu-id="b5770-149">DisplayStyle</span></span>|<xref:System.Windows.Forms.ToolStripItemDisplayStyle.ImageAndText>|  
    |<span data-ttu-id="b5770-150">ImageAlign</span><span class="sxs-lookup"><span data-stu-id="b5770-150">ImageAlign</span></span>|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
    |<span data-ttu-id="b5770-151">ImageScaling</span><span class="sxs-lookup"><span data-stu-id="b5770-151">ImageScaling</span></span>|<xref:System.Windows.Forms.ToolStripItemImageScaling.None>|  
    |<span data-ttu-id="b5770-152">ImageTransparentColor</span><span class="sxs-lookup"><span data-stu-id="b5770-152">ImageTransparentColor</span></span>|`238, 238, 238`|  
    |<span data-ttu-id="b5770-153">Margines</span><span class="sxs-lookup"><span data-stu-id="b5770-153">Margin</span></span>|`0, 0, 0, 0`|  
    |<span data-ttu-id="b5770-154">Dopełnienie</span><span class="sxs-lookup"><span data-stu-id="b5770-154">Padding</span></span>|`3, 3, 3, 3`|  
    |<span data-ttu-id="b5770-155">Tekst</span><span class="sxs-lookup"><span data-stu-id="b5770-155">Text</span></span>|<span data-ttu-id="b5770-156">**Poczty**</span><span class="sxs-lookup"><span data-stu-id="b5770-156">**Mail**</span></span>|  
    |<span data-ttu-id="b5770-157">TextAlign</span><span class="sxs-lookup"><span data-stu-id="b5770-157">TextAlign</span></span>|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
  
5.  <span data-ttu-id="b5770-158">Powtórz kroki od 7 do trzech więcej <xref:System.Windows.Forms.ToolStripButton> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="b5770-158">Repeat step 7 for three more <xref:System.Windows.Forms.ToolStripButton> controls.</span></span>  
  
     <span data-ttu-id="b5770-159">Nazwa kontrolki `calendarStackButton`, `contactsStackButton`, i `tasksStackButton`.</span><span class="sxs-lookup"><span data-stu-id="b5770-159">Name the controls `calendarStackButton`, `contactsStackButton`, and `tasksStackButton`.</span></span> <span data-ttu-id="b5770-160">Ustaw wartość <xref:System.Windows.Forms.Control.Text%2A> właściwości **kalendarza**, **kontaktów**, i **zadania**odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="b5770-160">Set the value of the <xref:System.Windows.Forms.Control.Text%2A> property to **Calendar**, **Contacts**, and **Tasks**, respectively.</span></span>  
  
## <a name="handling-events"></a><span data-ttu-id="b5770-161">Obsługa zdarzeń</span><span class="sxs-lookup"><span data-stu-id="b5770-161">Handling Events</span></span>  
 <span data-ttu-id="b5770-162">Dwa zdarzenia są ważne dla zapewnienia `StackView` kontroli zadziała poprawnie.</span><span class="sxs-lookup"><span data-stu-id="b5770-162">Two events are important to make the `StackView` control behave correctly.</span></span> <span data-ttu-id="b5770-163">Obsługa <xref:System.Windows.Forms.UserControl.Load> zdarzenie, aby poprawnie pozycji formantu.</span><span class="sxs-lookup"><span data-stu-id="b5770-163">Handle the <xref:System.Windows.Forms.UserControl.Load> event to position the control correctly.</span></span> <span data-ttu-id="b5770-164">Obsługa <xref:System.Windows.Forms.ToolStripItem.Click> zdarzeń dla każdego <xref:System.Windows.Forms.ToolStripButton> umożliwiają `StackView` kontrolowania podobne do zachowania stanu <xref:System.Windows.Forms.RadioButton> kontroli.</span><span class="sxs-lookup"><span data-stu-id="b5770-164">Handle the <xref:System.Windows.Forms.ToolStripItem.Click> event for each <xref:System.Windows.Forms.ToolStripButton> to give the `StackView` control state behavior similar to the <xref:System.Windows.Forms.RadioButton> control.</span></span>  
  
#### <a name="to-handle-events"></a><span data-ttu-id="b5770-165">Do obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="b5770-165">To handle events</span></span>  
  
1.  <span data-ttu-id="b5770-166">W narzędziu Projektant dla formularzy systemu Windows wybierz `StackView` formantu.</span><span class="sxs-lookup"><span data-stu-id="b5770-166">In the Windows Forms Designer, select the `StackView` control.</span></span>  
  
2.  <span data-ttu-id="b5770-167">W **właściwości** okna, kliknij przycisk **zdarzenia**.</span><span class="sxs-lookup"><span data-stu-id="b5770-167">In the **Properties** window, click **Events**.</span></span>  
  
3.  <span data-ttu-id="b5770-168">Kliknij dwukrotnie zdarzenie obciążenia, aby wygenerować `StackView_Load` obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b5770-168">Double-click the Load event to generate the `StackView_Load` event handler.</span></span>  
  
4.  <span data-ttu-id="b5770-169">W `StackView_Load` program obsługi zdarzeń, skopiuj i wklej poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="b5770-169">In the `StackView_Load` event handler, copy and paste the following code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#3)]  
  
5.  <span data-ttu-id="b5770-170">W narzędziu Projektant dla formularzy systemu Windows wybierz `mailStackButton` formantu.</span><span class="sxs-lookup"><span data-stu-id="b5770-170">In the Windows Forms Designer, select the `mailStackButton` control.</span></span>  
  
6.  <span data-ttu-id="b5770-171">W **właściwości** okna, kliknij przycisk **zdarzenia**.</span><span class="sxs-lookup"><span data-stu-id="b5770-171">In the **Properties** window, click **Events**.</span></span>  
  
7.  <span data-ttu-id="b5770-172">Kliknij dwukrotnie zdarzenie Click.</span><span class="sxs-lookup"><span data-stu-id="b5770-172">Double-click the Click event.</span></span>  
  
     <span data-ttu-id="b5770-173">Projektant formularzy systemu Windows generuje `mailStackButton_Click` obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b5770-173">The Windows Forms Designer generates the `mailStackButton_Click` event handler.</span></span>  
  
8.  <span data-ttu-id="b5770-174">Zmień nazwę `mailStackButton_Click` program obsługi zdarzeń do `stackButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="b5770-174">Rename the `mailStackButton_Click` event handler to `stackButton_Click`.</span></span>  
  
     <span data-ttu-id="b5770-175">Aby uzyskać więcej informacji, zobacz [porady: Zmienianie nazwy identyfikator (Visual Basic)](http://msdn.microsoft.com/library/e5a5edf8-3dba-4119-81f4-fc2aba180e0c).</span><span class="sxs-lookup"><span data-stu-id="b5770-175">For more information, see [How to: Rename an Identifier (Visual Basic)](http://msdn.microsoft.com/library/e5a5edf8-3dba-4119-81f4-fc2aba180e0c).</span></span>  
  
9. <span data-ttu-id="b5770-176">Wstaw następujący kod do `stackButton_Click` obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b5770-176">Insert the following code into the `stackButton_Click` event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#4)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#4)]  
  
10. <span data-ttu-id="b5770-177">W narzędziu Projektant dla formularzy systemu Windows wybierz `calendarStackButton` formantu.</span><span class="sxs-lookup"><span data-stu-id="b5770-177">In the Windows Forms Designer, select the `calendarStackButton` control.</span></span>  
  
11. <span data-ttu-id="b5770-178">W **właściwości** oknie ustawioną zdarzenie Click `stackButton_Click` obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b5770-178">In the **Properties** window, set the Click event to the `stackButton_Click` event handler.</span></span>  
  
12. <span data-ttu-id="b5770-179">Powtórz kroki od 10 i 11 dla `contactsStackButton` i `tasksStackButton` kontrolki.</span><span class="sxs-lookup"><span data-stu-id="b5770-179">Repeat steps 10 and 11 for the `contactsStackButton` and `tasksStackButton` controls.</span></span>  
  
## <a name="defining-icons"></a><span data-ttu-id="b5770-180">Definiowanie ikon</span><span class="sxs-lookup"><span data-stu-id="b5770-180">Defining Icons</span></span>  
 <span data-ttu-id="b5770-181">Każdy `StackView` przycisk ma skojarzona ikona.</span><span class="sxs-lookup"><span data-stu-id="b5770-181">Each `StackView` button has an associated icon.</span></span> <span data-ttu-id="b5770-182">Dla wygody, każda z ikon jest reprezentowany jako ciąg zakodowany w formacie Base64, którego deserializowany jest przed <xref:System.Drawing.Bitmap> jest tworzony z niego.</span><span class="sxs-lookup"><span data-stu-id="b5770-182">For convenience, each icon is represented as a Base64-encoded string, which is deserialized before a <xref:System.Drawing.Bitmap> is created from it.</span></span> <span data-ttu-id="b5770-183">W środowisku produkcyjnym przechowują dane mapy bitowej jako zasób i ikony wyświetlane w narzędziu Projektant dla formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b5770-183">In a production environment, you store bitmap data as a resource, and your icons appear in the Windows Forms Designer.</span></span> <span data-ttu-id="b5770-184">Aby uzyskać więcej informacji, zobacz [porady: Dodawanie obrazy tła do formularzy systemu Windows](http://msdn.microsoft.com/library/7a509ba2-055c-4ae6-b88a-54625c6d9aff).</span><span class="sxs-lookup"><span data-stu-id="b5770-184">For more information, see [How to: Add Background Images to Windows Forms](http://msdn.microsoft.com/library/7a509ba2-055c-4ae6-b88a-54625c6d9aff).</span></span>  
  
#### <a name="to-define-icons"></a><span data-ttu-id="b5770-185">Aby zdefiniować ikon</span><span class="sxs-lookup"><span data-stu-id="b5770-185">To define icons</span></span>  
  
1.  <span data-ttu-id="b5770-186">W edytorze kodu Wstaw następujący kod do `StackView` definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="b5770-186">In the Code Editor, insert the following code into the `StackView` class definition.</span></span> <span data-ttu-id="b5770-187">Ten kod inicjuje bitmap do <xref:System.Windows.Forms.ToolStripButton> ikon.</span><span class="sxs-lookup"><span data-stu-id="b5770-187">This code initializes the bitmaps for the <xref:System.Windows.Forms.ToolStripButton> icons.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#2)]  
  
2.  <span data-ttu-id="b5770-188">Dodaj wywołanie do `InitializeImages` metoda `StackView` konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="b5770-188">Add a call to the `InitializeImages` method in the `StackView` class constructor.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="implementing-a-custom-renderer"></a><span data-ttu-id="b5770-189">Implementowanie niestandardowego modułu renderowania</span><span class="sxs-lookup"><span data-stu-id="b5770-189">Implementing a Custom Renderer</span></span>  
 <span data-ttu-id="b5770-190">Można dostosować większość elementów `StackView` kontrolować Moje Implementacja klasy, która jest pochodną <xref:System.Windows.Forms.ToolStripRenderer> klasy.</span><span class="sxs-lookup"><span data-stu-id="b5770-190">You can customize most elements of the `StackView` control my implementing a class that derives from the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span> <span data-ttu-id="b5770-191">W tej procedurze zostaną zaimplementowane <xref:System.Windows.Forms.ToolStripProfessionalRenderer> klasy, która dostosowuje uchwytu i rysuje gradientu tła <xref:System.Windows.Forms.ToolStripButton> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="b5770-191">In this procedure, you will implement a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> class that customizes the grip and draws gradient backgrounds for the <xref:System.Windows.Forms.ToolStripButton> controls.</span></span>  
  
#### <a name="to-implement-a-custom-renderer"></a><span data-ttu-id="b5770-192">Aby zaimplementować niestandardowego modułu renderowania</span><span class="sxs-lookup"><span data-stu-id="b5770-192">To implement a custom renderer</span></span>  
  
1.  <span data-ttu-id="b5770-193">Wstaw następujący kod do `StackView` kontrolować definicji.</span><span class="sxs-lookup"><span data-stu-id="b5770-193">Insert the following code into the `StackView` control definition.</span></span>  
  
     <span data-ttu-id="b5770-194">Jest to definicja `StackRenderer` klasy, co zastępuje <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, i <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> metody do tworzenia niestandardowych wyglądu.</span><span class="sxs-lookup"><span data-stu-id="b5770-194">This is the definition for the `StackRenderer` class, which overrides the <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, and <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> methods to produce a custom appearance.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#10)]  
  
2.  <span data-ttu-id="b5770-195">W `StackView` konstruktora formantu, Utwórz nowe wystąpienie klasy `StackRenderer` klasy i przypisz tego wystąpienia `stackStrip` formantu <xref:System.Windows.Forms.ToolStrip.Renderer%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="b5770-195">In the `StackView` control's constructor, create a new instance of the `StackRenderer` class and assign this instance to the `stackStrip` control's <xref:System.Windows.Forms.ToolStrip.Renderer%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="testing-the-stackview-control"></a><span data-ttu-id="b5770-196">Testowanie formantu StackView</span><span class="sxs-lookup"><span data-stu-id="b5770-196">Testing the StackView Control</span></span>  
 <span data-ttu-id="b5770-197">`StackView` Formant pochodzi z <xref:System.Windows.Forms.UserControl> klasy.</span><span class="sxs-lookup"><span data-stu-id="b5770-197">The `StackView` control derives from the <xref:System.Windows.Forms.UserControl> class.</span></span> <span data-ttu-id="b5770-198">W związku z tym można przetestować kontrolki z **kontenera testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="b5770-198">Therefore, you can test the control with the **UserControl Test Container**.</span></span> <span data-ttu-id="b5770-199">Aby uzyskać więcej informacji, zobacz [porady: testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="b5770-199">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
#### <a name="to-test-the-stackview-control"></a><span data-ttu-id="b5770-200">Aby sprawdzić formant StackView</span><span class="sxs-lookup"><span data-stu-id="b5770-200">To test the StackView control</span></span>  
  
1.  <span data-ttu-id="b5770-201">Naciśnij klawisz F5, aby skompilować projekt i uruchomić **kontener testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="b5770-201">Press F5 to build the project and start the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="b5770-202">Przesuń wskaźnik myszy nad przycisków `StackView` kontroli, a następnie kliknij przycisk, aby zobaczyć wygląd stan zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="b5770-202">Move the pointer over the buttons of the `StackView` control, and then click a button to see the appearance of its selected state.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b5770-203">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="b5770-203">Next Steps</span></span>  
 <span data-ttu-id="b5770-204">W tym przewodniku utworzono kontrolki do ponownego użycia niestandardowego klienta profesjonalny wygląd formantu pakietu Office XP.</span><span class="sxs-lookup"><span data-stu-id="b5770-204">In this walkthrough, you have created a reusable custom client control with the professional appearance of an Office XP control.</span></span> <span data-ttu-id="b5770-205">Można użyć <xref:System.Windows.Forms.ToolStrip> rodziny formantów do innych celów:</span><span class="sxs-lookup"><span data-stu-id="b5770-205">You can use the <xref:System.Windows.Forms.ToolStrip> family of controls for many other purposes:</span></span>  
  
-   <span data-ttu-id="b5770-206">Tworzenie menu skrótów dla formantów z <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="b5770-206">Create shortcut menus for your controls with <xref:System.Windows.Forms.ContextMenuStrip>.</span></span> <span data-ttu-id="b5770-207">Aby uzyskać więcej informacji, zobacz [informacje o składniku ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="b5770-207">For more information, see [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="b5770-208">Tworzenie formularza z menu standardowego automatycznie wypełnione.</span><span class="sxs-lookup"><span data-stu-id="b5770-208">Create a form with an automatically populated standard menu.</span></span> <span data-ttu-id="b5770-209">Aby uzyskać więcej informacji, zobacz [wskazówki: zapewnianie standardowe elementy Menu do formularza](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span><span class="sxs-lookup"><span data-stu-id="b5770-209">For more information, see [Walkthrough: Providing Standard Menu Items to a Form](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).</span></span>  
  
-   <span data-ttu-id="b5770-210">Tworzenie wielu formularza interfejsu (MDI) dokumentu z dokowanie <xref:System.Windows.Forms.ToolStrip> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="b5770-210">Create a multiple document interface (MDI) form with docking <xref:System.Windows.Forms.ToolStrip> controls.</span></span> <span data-ttu-id="b5770-211">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie formularza MDI za pomocą scalania Menu i formantów ToolStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="b5770-211">For more information, see [How to: Create an MDI Form with Menu Merging and ToolStrip Controls](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5770-212">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b5770-212">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="b5770-213">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="b5770-213">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [<span data-ttu-id="b5770-214">Instrukcje: zapewnianie elementów menu standardowego dla formularza</span><span class="sxs-lookup"><span data-stu-id="b5770-214">How to: Provide Standard Menu Items to a Form</span></span>](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)
