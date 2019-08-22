---
title: 'Przewodnik: Rozmieszczanie zawartości WPF na formularzach systemu Windows w czasie projektowania'
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
ms.openlocfilehash: 7858ffd708c78d6397d533f613ccc2ea78d6cbed
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658521"
---
# <a name="walkthrough-arrange-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="173c8-102">Przewodnik: Rozmieszczanie zawartości WPF na Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="173c8-102">Walkthrough: Arrange WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="173c8-103">W tym artykule pokazano, jak używać funkcji układu Windows Forms, takich jak kotwice i linii wyrównania, aby rozmieścić kontrolki Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="173c8-103">This article shows you how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation (WPF) controls.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="173c8-104">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="173c8-104">Prerequisites</span></span>

<span data-ttu-id="173c8-105">Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="173c8-105">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="173c8-106">Utwórz projekt</span><span class="sxs-lookup"><span data-stu-id="173c8-106">Create the project</span></span>

<span data-ttu-id="173c8-107">Otwórz program Visual Studio i Utwórz nowy projekt aplikacji Windows Forms w Visual Basic lub C# wizualizacji `ArrangeElementHost`o nazwie.</span><span class="sxs-lookup"><span data-stu-id="173c8-107">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `ArrangeElementHost`.</span></span>

> [!NOTE]
> <span data-ttu-id="173c8-108">W przypadku hostowania zawartości WPF C# obsługiwane są tylko projekty i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="173c8-108">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control"></a><span data-ttu-id="173c8-109">Tworzenie kontrolki WPF</span><span class="sxs-lookup"><span data-stu-id="173c8-109">Create the WPF control</span></span>

<span data-ttu-id="173c8-110">Po dodaniu kontrolki WPF do projektu można ją rozmieścić w formularzu.</span><span class="sxs-lookup"><span data-stu-id="173c8-110">After you add a WPF control to the project, you can arrange it on the form.</span></span>

1. <span data-ttu-id="173c8-111">Dodaj nową WPF <xref:System.Windows.Controls.UserControl> do projektu.</span><span class="sxs-lookup"><span data-stu-id="173c8-111">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="173c8-112">Użyj domyślnej nazwy dla typu formantu, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="173c8-112">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="173c8-113">Aby uzyskać więcej informacji, [zobacz Przewodnik: Tworzenie nowej zawartości WPF na Windows Forms w czasie](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)projektowania.</span><span class="sxs-lookup"><span data-stu-id="173c8-113">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="173c8-114">W widok Projekt upewnij się, że `UserControl1` jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="173c8-114">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="173c8-115">W oknie **Właściwości** ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> właściwości i <xref:System.Windows.FrameworkElement.Height%2A> na **200**.</span><span class="sxs-lookup"><span data-stu-id="173c8-115">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="173c8-116">Ustaw wartość <xref:System.Windows.Controls.Control.Background%2A> właściwości na niebieską.</span><span class="sxs-lookup"><span data-stu-id="173c8-116">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to **Blue**.</span></span>

5. <span data-ttu-id="173c8-117">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="173c8-117">Build the project.</span></span>

## <a name="host-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="173c8-118">Hostowanie formantów WPF w panelu układu</span><span class="sxs-lookup"><span data-stu-id="173c8-118">Host WPF controls in a layout panel</span></span>

<span data-ttu-id="173c8-119">W panelach układów można używać formantów WPF w taki sam sposób, jak w przypadku innych kontrolek Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="173c8-119">You can use WPF controls in layout panels in the same way you use other Windows Forms controls.</span></span>

1. <span data-ttu-id="173c8-120">Otwórz `Form1` w Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="173c8-120">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="173c8-121">W **przyborniku**przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> kontrolkę na formularz.</span><span class="sxs-lookup"><span data-stu-id="173c8-121">In the **Toolbox**, drag a <xref:System.Windows.Forms.TableLayoutPanel> control onto the form.</span></span>

3. <span data-ttu-id="173c8-122">Na panelu tagu inteligentnego kontrolkiwybierzpozycjęUsuńostatni<xref:System.Windows.Forms.TableLayoutPanel> wiersz.</span><span class="sxs-lookup"><span data-stu-id="173c8-122">On the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag panel, select **Remove Last Row**.</span></span>

4. <span data-ttu-id="173c8-123">Zmień rozmiar <xref:System.Windows.Forms.TableLayoutPanel> kontrolki na większą szerokość i wysokość.</span><span class="sxs-lookup"><span data-stu-id="173c8-123">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger width and height.</span></span>

5. <span data-ttu-id="173c8-124">W **przyborniku**kliknij `UserControl1` dwukrotnie, aby utworzyć wystąpienie elementu `UserControl1` w pierwszej komórce <xref:System.Windows.Forms.TableLayoutPanel> formantu.</span><span class="sxs-lookup"><span data-stu-id="173c8-124">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` in the first cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

   <span data-ttu-id="173c8-125">Wystąpienie `UserControl1` jest hostowane w nowym <xref:System.Windows.Forms.Integration.ElementHost> formancie o nazwie `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="173c8-125">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

6. <span data-ttu-id="173c8-126">W **przyborniku**kliknij `UserControl1` dwukrotnie, aby utworzyć inne wystąpienie w <xref:System.Windows.Forms.TableLayoutPanel> drugiej komórce formantu.</span><span class="sxs-lookup"><span data-stu-id="173c8-126">In the **Toolbox**, double-click `UserControl1` to create another instance in the second cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

7. <span data-ttu-id="173c8-127">W oknie **Konspekt dokumentu** wybierz opcję `tableLayoutPanel1`.</span><span class="sxs-lookup"><span data-stu-id="173c8-127">In the **Document Outline** window, select `tableLayoutPanel1`.</span></span>

8. <span data-ttu-id="173c8-128">W oknie **Właściwości** ustaw wartość <xref:System.Windows.Forms.Control.Padding%2A> właściwości na **10, 10, 10, 10**.</span><span class="sxs-lookup"><span data-stu-id="173c8-128">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Padding%2A> property to **10, 10, 10, 10**.</span></span>

   <span data-ttu-id="173c8-129">Oba <xref:System.Windows.Forms.Integration.ElementHost> kontrolki są zmieniane w celu dopasowania do nowego układu.</span><span class="sxs-lookup"><span data-stu-id="173c8-129">Both <xref:System.Windows.Forms.Integration.ElementHost> controls are resized to fit into the new layout.</span></span>

## <a name="use-snaplines-to-align-wpf-controls"></a><span data-ttu-id="173c8-130">Użyj linii wyrównania do wyrównania formantów WPF</span><span class="sxs-lookup"><span data-stu-id="173c8-130">Use snaplines to align WPF controls</span></span>

<span data-ttu-id="173c8-131">Linii wyrównania umożliwia łatwe wyrównywanie kontrolek w formularzu.</span><span class="sxs-lookup"><span data-stu-id="173c8-131">Snaplines enable easy alignment of controls on a form.</span></span> <span data-ttu-id="173c8-132">Możesz użyć linii wyrównania, aby również wyrównać formanty WPF.</span><span class="sxs-lookup"><span data-stu-id="173c8-132">You can use snaplines to align your WPF controls as well.</span></span> <span data-ttu-id="173c8-133">Aby uzyskać więcej informacji, [zobacz Przewodnik: Rozmieszczanie kontrolek na Windows Forms](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)przy użyciu linii wyrównania.</span><span class="sxs-lookup"><span data-stu-id="173c8-133">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

1. <span data-ttu-id="173c8-134">Z **przybornika**przeciągnij wystąpienie do `UserControl1` formularza i umieść je w miejscu pod <xref:System.Windows.Forms.TableLayoutPanel> kontrolką.</span><span class="sxs-lookup"><span data-stu-id="173c8-134">From the **Toolbox**, drag an instance of `UserControl1` onto the form, and place it in the space beneath the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

   <span data-ttu-id="173c8-135">Wystąpienie `UserControl1` jest hostowane w nowym <xref:System.Windows.Forms.Integration.ElementHost> formancie o nazwie `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="173c8-135">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost3`.</span></span>

2. <span data-ttu-id="173c8-136">Przy użyciu linii wyrównania, Wyrównaj lewą krawędź `elementHost3` z lewej <xref:System.Windows.Forms.TableLayoutPanel> krawędzią kontrolki.</span><span class="sxs-lookup"><span data-stu-id="173c8-136">Using snaplines, align the left edge of `elementHost3` with the left edge of <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

3. <span data-ttu-id="173c8-137">Przy użyciu linii wyrównania, `elementHost3` rozmiar do tej samej szerokości <xref:System.Windows.Forms.TableLayoutPanel> jak kontrolka.</span><span class="sxs-lookup"><span data-stu-id="173c8-137">Using snaplines, size `elementHost3` to the same width as the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

4. <span data-ttu-id="173c8-138">Poruszanie `elementHost3` się <xref:System.Windows.Forms.TableLayoutPanel> w kierunku kontroli do momentu pojawienia się środkowego snapline między kontrolkami.</span><span class="sxs-lookup"><span data-stu-id="173c8-138">Move `elementHost3` toward the <xref:System.Windows.Forms.TableLayoutPanel> control until a center snapline appears between the controls.</span></span>

5. <span data-ttu-id="173c8-139">W oknie **Właściwości** ustaw wartość właściwości Margin na **20, 20, 20, 20**.</span><span class="sxs-lookup"><span data-stu-id="173c8-139">In the **Properties** window, set the value of the Margin property to **20, 20, 20, 20**.</span></span>

6. <span data-ttu-id="173c8-140">Przesuń z powrotem z kontrolki do momentu, gdy zostanie wyświetlone okno Center snapline. <xref:System.Windows.Forms.TableLayoutPanel> `elementHost3`</span><span class="sxs-lookup"><span data-stu-id="173c8-140">Move the `elementHost3` away from the <xref:System.Windows.Forms.TableLayoutPanel> control until the center snapline appears again.</span></span> <span data-ttu-id="173c8-141">Centrum snapline teraz wskazuje margines 20.</span><span class="sxs-lookup"><span data-stu-id="173c8-141">The center snapline now indicates a margin of 20.</span></span>

7. <span data-ttu-id="173c8-142">Przejście `elementHost3` w prawo do momentu, aż jego lewa krawędź zostanie wyrównana do lewej `elementHost1`krawędzi.</span><span class="sxs-lookup"><span data-stu-id="173c8-142">Move `elementHost3` to the right until its left edge aligns with the left edge of `elementHost1`.</span></span>

8. <span data-ttu-id="173c8-143">Zmień szerokość `elementHost3` do wyrównania `elementHost2`do prawej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="173c8-143">Change the width of `elementHost3` until its right edge aligns with the right edge of `elementHost2`.</span></span>

## <a name="anchor-and-dock-wpf-controls"></a><span data-ttu-id="173c8-144">Zakotwiczenie i dokowanie formantów WPF</span><span class="sxs-lookup"><span data-stu-id="173c8-144">Anchor and dock WPF controls</span></span>

<span data-ttu-id="173c8-145">Kontrolka WPF hostowana w formularzu ma takie samo zachowanie dotyczące zakotwiczania i dokowania jak inne kontrolki Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="173c8-145">A WPF control hosted on a form has the same anchoring and docking behavior as other Windows Forms controls.</span></span>

1. <span data-ttu-id="173c8-146">Wybierz `elementHost1`opcję.</span><span class="sxs-lookup"><span data-stu-id="173c8-146">Select `elementHost1`.</span></span>

2. <span data-ttu-id="173c8-147">W oknie **Właściwości** Ustaw <xref:System.Windows.Forms.Control.Anchor%2A> właściwość na **Top, Bottom, Left, Right**.</span><span class="sxs-lookup"><span data-stu-id="173c8-147">In the **Properties** window, set the <xref:System.Windows.Forms.Control.Anchor%2A> property to **Top, Bottom, Left, Right**.</span></span>

3. <span data-ttu-id="173c8-148">Zmień rozmiar <xref:System.Windows.Forms.TableLayoutPanel> kontrolki na większy.</span><span class="sxs-lookup"><span data-stu-id="173c8-148">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger size.</span></span>

   <span data-ttu-id="173c8-149">Zmienia `elementHost1` rozmiar kontrolki w celu wypełnienia komórki.</span><span class="sxs-lookup"><span data-stu-id="173c8-149">The `elementHost1` control resizes to fill the cell.</span></span>

4. <span data-ttu-id="173c8-150">Wybierz `elementHost2`opcję.</span><span class="sxs-lookup"><span data-stu-id="173c8-150">Select `elementHost2`.</span></span>

5. <span data-ttu-id="173c8-151">W oknie **Właściwości** ustaw wartość <xref:System.Windows.Forms.Control.Dock%2A> właściwości na <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="173c8-151">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

   <span data-ttu-id="173c8-152">Zmienia `elementHost2` rozmiar kontrolki w celu wypełnienia komórki.</span><span class="sxs-lookup"><span data-stu-id="173c8-152">The `elementHost2` control resizes to fill the cell.</span></span>

6. <span data-ttu-id="173c8-153"><xref:System.Windows.Forms.TableLayoutPanel> Zaznacz kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="173c8-153">Select the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

7. <span data-ttu-id="173c8-154">Ustaw wartość <xref:System.Windows.Forms.Control.Dock%2A> właściwości na <xref:System.Windows.Forms.DockStyle.Top>.</span><span class="sxs-lookup"><span data-stu-id="173c8-154">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Top>.</span></span>

8. <span data-ttu-id="173c8-155">Wybierz `elementHost3`opcję.</span><span class="sxs-lookup"><span data-stu-id="173c8-155">Select `elementHost3`.</span></span>

9. <span data-ttu-id="173c8-156">Ustaw wartość <xref:System.Windows.Forms.Control.Dock%2A> właściwości na <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="173c8-156">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

   <span data-ttu-id="173c8-157">Zmienia `elementHost3` rozmiar kontrolki w celu wypełnienia pozostałego miejsca w formularzu.</span><span class="sxs-lookup"><span data-stu-id="173c8-157">The `elementHost3` control resizes to fill the remaining space on the form.</span></span>

10. <span data-ttu-id="173c8-158">Zmień rozmiar formularza.</span><span class="sxs-lookup"><span data-stu-id="173c8-158">Resize the form.</span></span>

    <span data-ttu-id="173c8-159">Wszystkie trzy <xref:System.Windows.Forms.Integration.ElementHost> kontrolki odpowiednio zmieniają rozmiar.</span><span class="sxs-lookup"><span data-stu-id="173c8-159">All three <xref:System.Windows.Forms.Integration.ElementHost> controls resize appropriately.</span></span>

    <span data-ttu-id="173c8-160">Aby uzyskać więcej informacji, zobacz [jak: Zakotwiczenie i dokowanie formantów podrzędnych w formancie](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)TableLayoutPanel.</span><span class="sxs-lookup"><span data-stu-id="173c8-160">For more information, see [How to: Anchor and Dock Child Controls in a TableLayoutPanel Control](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="173c8-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="173c8-161">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="173c8-162">Instrukcje: Zakotwiczenie i dokowanie formantów podrzędnych w formancie TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="173c8-162">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="173c8-163">Instrukcje: Wyrównywanie kontrolki do krawędzi formularzy w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="173c8-163">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [<span data-ttu-id="173c8-164">Przewodnik: Rozmieszczanie kontrolek na Windows Forms przy użyciu linii wyrównania</span><span class="sxs-lookup"><span data-stu-id="173c8-164">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="173c8-165">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="173c8-165">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="173c8-166">Korzystanie z kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="173c8-166">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="173c8-167">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="173c8-167">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
