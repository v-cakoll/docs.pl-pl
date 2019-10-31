---
title: 'Wskazówki: rozmieszczanie zawartości WPF na formularzach systemu Windows w czasie projektowania'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9062a3da9a6020762114702b6cce6b42414ab92d
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197458"
---
# <a name="walkthrough-arrange-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="40d81-102">Przewodnik: rozmieszczanie zawartości WPF na Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="40d81-102">Walkthrough: Arrange WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="40d81-103">W tym artykule pokazano, jak używać funkcji układu Windows Forms, takich jak kotwice i linii wyrównania, aby rozmieścić kontrolki Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="40d81-103">This article shows you how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation (WPF) controls.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="40d81-104">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="40d81-104">Prerequisites</span></span>

<span data-ttu-id="40d81-105">Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="40d81-105">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="40d81-106">Utwórz projekt</span><span class="sxs-lookup"><span data-stu-id="40d81-106">Create the project</span></span>

<span data-ttu-id="40d81-107">Otwórz program Visual Studio i Utwórz nowy projekt aplikacji Windows Forms w Visual Basic lub wizualizacji C# o nazwie `ArrangeElementHost`.</span><span class="sxs-lookup"><span data-stu-id="40d81-107">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `ArrangeElementHost`.</span></span>

> [!NOTE]
> <span data-ttu-id="40d81-108">W przypadku hostowania zawartości WPF C# obsługiwane są tylko projekty i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="40d81-108">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control"></a><span data-ttu-id="40d81-109">Tworzenie kontrolki WPF</span><span class="sxs-lookup"><span data-stu-id="40d81-109">Create the WPF control</span></span>

<span data-ttu-id="40d81-110">Po dodaniu kontrolki WPF do projektu można ją rozmieścić w formularzu.</span><span class="sxs-lookup"><span data-stu-id="40d81-110">After you add a WPF control to the project, you can arrange it on the form.</span></span>

1. <span data-ttu-id="40d81-111">Dodaj nowy <xref:System.Windows.Controls.UserControl> WPF do projektu.</span><span class="sxs-lookup"><span data-stu-id="40d81-111">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="40d81-112">Użyj domyślnej nazwy dla typu formantu, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="40d81-112">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="40d81-113">Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie nowej zawartości WPF na Windows Forms w czasie projektowania](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="40d81-113">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="40d81-114">W widok Projekt upewnij się, że wybrano pozycję `UserControl1`.</span><span class="sxs-lookup"><span data-stu-id="40d81-114">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="40d81-115">W oknie **Właściwości** ustaw wartość właściwości <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> na **200**.</span><span class="sxs-lookup"><span data-stu-id="40d81-115">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="40d81-116">Ustaw wartość właściwości <xref:System.Windows.Controls.Control.Background%2A> na **niebieską**.</span><span class="sxs-lookup"><span data-stu-id="40d81-116">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to **Blue**.</span></span>

5. <span data-ttu-id="40d81-117">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="40d81-117">Build the project.</span></span>

## <a name="host-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="40d81-118">Hostowanie formantów WPF w panelu układu</span><span class="sxs-lookup"><span data-stu-id="40d81-118">Host WPF controls in a layout panel</span></span>

<span data-ttu-id="40d81-119">W panelach układów można używać formantów WPF w taki sam sposób, jak w przypadku innych kontrolek Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="40d81-119">You can use WPF controls in layout panels in the same way you use other Windows Forms controls.</span></span>

1. <span data-ttu-id="40d81-120">Otwórz `Form1` w Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="40d81-120">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="40d81-121">W **przyborniku**przeciągnij kontrolkę <xref:System.Windows.Forms.TableLayoutPanel> na formularz.</span><span class="sxs-lookup"><span data-stu-id="40d81-121">In the **Toolbox**, drag a <xref:System.Windows.Forms.TableLayoutPanel> control onto the form.</span></span>

3. <span data-ttu-id="40d81-122">Na panelu tagów inteligentnych kontrolki <xref:System.Windows.Forms.TableLayoutPanel> wybierz pozycję **Usuń ostatni wiersz**.</span><span class="sxs-lookup"><span data-stu-id="40d81-122">On the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag panel, select **Remove Last Row**.</span></span>

4. <span data-ttu-id="40d81-123">Zmień rozmiar kontrolki <xref:System.Windows.Forms.TableLayoutPanel> na większą szerokość i wysokość.</span><span class="sxs-lookup"><span data-stu-id="40d81-123">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger width and height.</span></span>

5. <span data-ttu-id="40d81-124">W **przyborniku**kliknij dwukrotnie `UserControl1`, aby utworzyć wystąpienie `UserControl1` w pierwszej komórce kontrolki <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="40d81-124">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` in the first cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

   <span data-ttu-id="40d81-125">Wystąpienie `UserControl1` jest hostowane w nowej kontrolce <xref:System.Windows.Forms.Integration.ElementHost> o nazwie `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="40d81-125">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

6. <span data-ttu-id="40d81-126">W **przyborniku**kliknij dwukrotnie `UserControl1`, aby utworzyć inne wystąpienie w drugiej komórce kontrolki <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="40d81-126">In the **Toolbox**, double-click `UserControl1` to create another instance in the second cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

7. <span data-ttu-id="40d81-127">W oknie **Konspekt dokumentu** wybierz pozycję `tableLayoutPanel1`.</span><span class="sxs-lookup"><span data-stu-id="40d81-127">In the **Document Outline** window, select `tableLayoutPanel1`.</span></span>

8. <span data-ttu-id="40d81-128">W oknie **Właściwości** ustaw wartość właściwości <xref:System.Windows.Forms.Control.Padding%2A> na **10, 10, 10, 10**.</span><span class="sxs-lookup"><span data-stu-id="40d81-128">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Padding%2A> property to **10, 10, 10, 10**.</span></span>

   <span data-ttu-id="40d81-129">Zmiany rozmiaru obu formantów <xref:System.Windows.Forms.Integration.ElementHost> są dopasowane do nowego układu.</span><span class="sxs-lookup"><span data-stu-id="40d81-129">Both <xref:System.Windows.Forms.Integration.ElementHost> controls are resized to fit into the new layout.</span></span>

## <a name="use-snaplines-to-align-wpf-controls"></a><span data-ttu-id="40d81-130">Użyj linii wyrównania do wyrównania formantów WPF</span><span class="sxs-lookup"><span data-stu-id="40d81-130">Use snaplines to align WPF controls</span></span>

<span data-ttu-id="40d81-131">Linii wyrównania umożliwia łatwe wyrównywanie kontrolek w formularzu.</span><span class="sxs-lookup"><span data-stu-id="40d81-131">Snaplines enable easy alignment of controls on a form.</span></span> <span data-ttu-id="40d81-132">Możesz użyć linii wyrównania, aby również wyrównać formanty WPF.</span><span class="sxs-lookup"><span data-stu-id="40d81-132">You can use snaplines to align your WPF controls as well.</span></span> <span data-ttu-id="40d81-133">Aby uzyskać więcej informacji, zobacz [Przewodnik: rozmieszczanie formantów na Windows Forms przy użyciu linii wyrównania](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="40d81-133">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

1. <span data-ttu-id="40d81-134">Z **przybornika**przeciągnij wystąpienie `UserControl1` na formularz i umieść je w miejscu poniżej kontrolki <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="40d81-134">From the **Toolbox**, drag an instance of `UserControl1` onto the form, and place it in the space beneath the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

   <span data-ttu-id="40d81-135">Wystąpienie `UserControl1` jest hostowane w nowej kontrolce <xref:System.Windows.Forms.Integration.ElementHost> o nazwie `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="40d81-135">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost3`.</span></span>

2. <span data-ttu-id="40d81-136">Korzystając z linii wyrównania, Wyrównaj lewą krawędź `elementHost3` z lewą krawędzią <xref:System.Windows.Forms.TableLayoutPanel> formantu.</span><span class="sxs-lookup"><span data-stu-id="40d81-136">Using snaplines, align the left edge of `elementHost3` with the left edge of <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

3. <span data-ttu-id="40d81-137">Przy użyciu linii wyrównania rozmiar `elementHost3` ma taką samą szerokość jak kontrolka <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="40d81-137">Using snaplines, size `elementHost3` to the same width as the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

4. <span data-ttu-id="40d81-138">Przenieś `elementHost3` do kontrolki <xref:System.Windows.Forms.TableLayoutPanel> do momentu pojawienia się środkowej snapline między kontrolkami.</span><span class="sxs-lookup"><span data-stu-id="40d81-138">Move `elementHost3` toward the <xref:System.Windows.Forms.TableLayoutPanel> control until a center snapline appears between the controls.</span></span>

5. <span data-ttu-id="40d81-139">W oknie **Właściwości** ustaw wartość właściwości Margin na **20, 20, 20, 20**.</span><span class="sxs-lookup"><span data-stu-id="40d81-139">In the **Properties** window, set the value of the Margin property to **20, 20, 20, 20**.</span></span>

6. <span data-ttu-id="40d81-140">Przenieś `elementHost3` z powrotem do kontrolki <xref:System.Windows.Forms.TableLayoutPanel> do momentu, aż zostanie wyświetlone centrum snapline.</span><span class="sxs-lookup"><span data-stu-id="40d81-140">Move the `elementHost3` away from the <xref:System.Windows.Forms.TableLayoutPanel> control until the center snapline appears again.</span></span> <span data-ttu-id="40d81-141">Centrum snapline teraz wskazuje margines 20.</span><span class="sxs-lookup"><span data-stu-id="40d81-141">The center snapline now indicates a margin of 20.</span></span>

7. <span data-ttu-id="40d81-142">Przenieś `elementHost3` w prawo do momentu, aż lewa krawędź wyrównuje z lewą krawędzią `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="40d81-142">Move `elementHost3` to the right until its left edge aligns with the left edge of `elementHost1`.</span></span>

8. <span data-ttu-id="40d81-143">Zmień szerokość `elementHost3` do momentu, aż jego prawa krawędź wyrównuje z prawą krawędzią `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="40d81-143">Change the width of `elementHost3` until its right edge aligns with the right edge of `elementHost2`.</span></span>

## <a name="anchor-and-dock-wpf-controls"></a><span data-ttu-id="40d81-144">Zakotwiczenie i dokowanie formantów WPF</span><span class="sxs-lookup"><span data-stu-id="40d81-144">Anchor and dock WPF controls</span></span>

<span data-ttu-id="40d81-145">Kontrolka WPF hostowana w formularzu ma takie samo zachowanie dotyczące zakotwiczania i dokowania jak inne kontrolki Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="40d81-145">A WPF control hosted on a form has the same anchoring and docking behavior as other Windows Forms controls.</span></span>

1. <span data-ttu-id="40d81-146">Wybierz `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="40d81-146">Select `elementHost1`.</span></span>

2. <span data-ttu-id="40d81-147">W oknie **Właściwości** ustaw właściwość <xref:System.Windows.Forms.Control.Anchor%2A> na **Top, Bottom, Left, Right**.</span><span class="sxs-lookup"><span data-stu-id="40d81-147">In the **Properties** window, set the <xref:System.Windows.Forms.Control.Anchor%2A> property to **Top, Bottom, Left, Right**.</span></span>

3. <span data-ttu-id="40d81-148">Zmień rozmiar kontrolki <xref:System.Windows.Forms.TableLayoutPanel> na większy.</span><span class="sxs-lookup"><span data-stu-id="40d81-148">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger size.</span></span>

   <span data-ttu-id="40d81-149">Formant `elementHost1` zmienia rozmiar, aby wypełnić komórkę.</span><span class="sxs-lookup"><span data-stu-id="40d81-149">The `elementHost1` control resizes to fill the cell.</span></span>

4. <span data-ttu-id="40d81-150">Wybierz `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="40d81-150">Select `elementHost2`.</span></span>

5. <span data-ttu-id="40d81-151">W oknie **Właściwości** ustaw wartość właściwości <xref:System.Windows.Forms.Control.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="40d81-151">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

   <span data-ttu-id="40d81-152">Formant `elementHost2` zmienia rozmiar, aby wypełnić komórkę.</span><span class="sxs-lookup"><span data-stu-id="40d81-152">The `elementHost2` control resizes to fill the cell.</span></span>

6. <span data-ttu-id="40d81-153">Wybierz kontrolkę <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="40d81-153">Select the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

7. <span data-ttu-id="40d81-154">Ustaw wartość właściwości <xref:System.Windows.Forms.Control.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Top>.</span><span class="sxs-lookup"><span data-stu-id="40d81-154">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Top>.</span></span>

8. <span data-ttu-id="40d81-155">Wybierz `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="40d81-155">Select `elementHost3`.</span></span>

9. <span data-ttu-id="40d81-156">Ustaw wartość właściwości <xref:System.Windows.Forms.Control.Dock%2A> na <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="40d81-156">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

   <span data-ttu-id="40d81-157">Kontrolka `elementHost3` zmienia rozmiar w celu wypełnienia pozostałego miejsca w formularzu.</span><span class="sxs-lookup"><span data-stu-id="40d81-157">The `elementHost3` control resizes to fill the remaining space on the form.</span></span>

10. <span data-ttu-id="40d81-158">Zmień rozmiar formularza.</span><span class="sxs-lookup"><span data-stu-id="40d81-158">Resize the form.</span></span>

    <span data-ttu-id="40d81-159">Wszystkie trzy <xref:System.Windows.Forms.Integration.ElementHost> kontrolki odpowiednio zmieniają rozmiar.</span><span class="sxs-lookup"><span data-stu-id="40d81-159">All three <xref:System.Windows.Forms.Integration.ElementHost> controls resize appropriately.</span></span>

    <span data-ttu-id="40d81-160">Aby uzyskać więcej informacji, zobacz [How to: Zakotwiczanie i dokowanie formantów podrzędnych w formancie TableLayoutPanel](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span><span class="sxs-lookup"><span data-stu-id="40d81-160">For more information, see [How to: Anchor and Dock Child Controls in a TableLayoutPanel Control](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="40d81-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40d81-161">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="40d81-162">Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="40d81-162">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="40d81-163">Instrukcje: wyrównywanie kontrolki z krawędziami formularzy w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="40d81-163">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [<span data-ttu-id="40d81-164">Przewodnik: rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania</span><span class="sxs-lookup"><span data-stu-id="40d81-164">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="40d81-165">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="40d81-165">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="40d81-166">Korzystanie z kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="40d81-166">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="40d81-167">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="40d81-167">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
