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
ms.openlocfilehash: a8f690438136450cb12dbcf5e17ddfcca617457e
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211444"
---
# <a name="walkthrough-arrange-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="f3fb3-102">Przewodnik: Rozmieszczanie zawartości WPF na formularzach Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="f3fb3-102">Walkthrough: Arrange WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="f3fb3-103">W tym instruktażu przedstawiono sposób korzystania z funkcji układu formularzy Windows, takich jak Zakotwiczanie i linii przyciągania, aby rozmieścić formanty Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="f3fb3-103">This walkthrough shows you how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation (WPF) controls.</span></span>

<span data-ttu-id="f3fb3-104">W tym przewodniku należy wykonać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="f3fb3-104">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="f3fb3-105">Utwórz projekt.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-105">Create the project.</span></span>

- <span data-ttu-id="f3fb3-106">Tworzenie formantu WPF.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-106">Create the WPF control.</span></span>

- <span data-ttu-id="f3fb3-107">Host formantów WPF w panelu układu.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-107">Host WPF controls in a layout panel.</span></span>

- <span data-ttu-id="f3fb3-108">Linii przyciągania użycia do wyrównania kontrolek WPF.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-108">Use snaplines to align WPF controls.</span></span>

- <span data-ttu-id="f3fb3-109">Zakotwiczenie i dokowanie kontrolek WPF.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-109">Anchor and dock WPF controls.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f3fb3-110">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="f3fb3-110">Prerequisites</span></span>

<span data-ttu-id="f3fb3-111">Potrzebujesz programu Visual Studio w celu przeprowadzenia tego instruktażu.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-111">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="f3fb3-112">Utwórz projekt</span><span class="sxs-lookup"><span data-stu-id="f3fb3-112">Create the project</span></span>

<span data-ttu-id="f3fb3-113">Otwórz program Visual Studio i Utwórz nowy projekt Windows Forms aplikacji w Visual Basic lub Visual C# o nazwie `ArrangeElementHost`.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-113">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `ArrangeElementHost`.</span></span>

> [!NOTE]
> <span data-ttu-id="f3fb3-114">Gdy hosting zawartości WPF, obsługiwane są tylko C# i projektach języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-114">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control"></a><span data-ttu-id="f3fb3-115">Tworzenie kontrolki WPF</span><span class="sxs-lookup"><span data-stu-id="f3fb3-115">Create the WPF control</span></span>

<span data-ttu-id="f3fb3-116">Po dodaniu kontrolki WPF do projektu, można rozmieścić je na formularzu.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-116">After you add a WPF control to the project, you can arrange it on the form.</span></span>

1. <span data-ttu-id="f3fb3-117">Dodaj nowe WPF <xref:System.Windows.Controls.UserControl> do projektu.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-117">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="f3fb3-118">Użyj domyślnej nazwy dla kontrolek typu `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-118">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="f3fb3-119">Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie nowej zawartości WPF na formularzach Windows Forms w czasie projektowania](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="f3fb3-119">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="f3fb3-120">W widoku Projekt, upewnij się, że `UserControl1` jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-120">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="f3fb3-121">Aby uzyskać więcej informacji, zobacz [jak: Wybierz i Przesuń elementy na powierzchni projektowej](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="f3fb3-121">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>

3. <span data-ttu-id="f3fb3-122">W **właściwości** okna, ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości `200`.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-122">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>

4. <span data-ttu-id="f3fb3-123">Ustaw wartość <xref:System.Windows.Controls.Control.Background%2A> właściwość `Blue`.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-123">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>

5. <span data-ttu-id="f3fb3-124">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-124">Build the project.</span></span>

## <a name="hosting-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="f3fb3-125">Hosting kontrolek WPF w panelu układu</span><span class="sxs-lookup"><span data-stu-id="f3fb3-125">Hosting WPF Controls in a Layout Panel</span></span>
 <span data-ttu-id="f3fb3-126">Umożliwia kontrolek WPF w panele układów w taki sam sposób, jak używać innych kontrolek Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-126">You can use WPF controls in layout panels in the same way you use other Windows Forms controls.</span></span>

#### <a name="to-host-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="f3fb3-127">Host formantów WPF w panelu układu</span><span class="sxs-lookup"><span data-stu-id="f3fb3-127">To host WPF controls in a layout panel</span></span>

1. <span data-ttu-id="f3fb3-128">Otwórz `Form1` w programie Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-128">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="f3fb3-129">W **przybornika**, przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> formant na formularzu.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-129">In the **Toolbox**, drag a <xref:System.Windows.Forms.TableLayoutPanel> control onto the form.</span></span>

3. <span data-ttu-id="f3fb3-130">Na <xref:System.Windows.Forms.TableLayoutPanel> kontrolki panelu tagi inteligentne, wybierz **Usuń ostatni wiersz**.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-130">On the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag panel, select **Remove Last Row**.</span></span>

4. <span data-ttu-id="f3fb3-131">Zmień rozmiar <xref:System.Windows.Forms.TableLayoutPanel> kontrolki większych szerokość i wysokość.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-131">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger width and height.</span></span>

5. <span data-ttu-id="f3fb3-132">W **przybornika**, kliknij dwukrotnie `UserControl1` do utworzenia wystąpienia `UserControl1` w pierwszej komórki z <xref:System.Windows.Forms.TableLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-132">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` in the first cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

     <span data-ttu-id="f3fb3-133">Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-133">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

6. <span data-ttu-id="f3fb3-134">W **przybornika**, kliknij dwukrotnie `UserControl1` Aby utworzyć inną instancję w drugiej komórce <xref:System.Windows.Forms.TableLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-134">In the **Toolbox**, double-click `UserControl1` to create another instance in the second cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

7. <span data-ttu-id="f3fb3-135">W **konspekt dokumentu** wybierz `tableLayoutPanel1`.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-135">In the **Document Outline** window, select `tableLayoutPanel1`.</span></span> <span data-ttu-id="f3fb3-136">Aby uzyskać więcej informacji, zobacz [okno konspektu dokumentu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/46xf4h0w(v=vs.100)#using-the-document-outline-window-for-silverlight-and-wpf).</span><span class="sxs-lookup"><span data-stu-id="f3fb3-136">For more information, see [Document Outline Window](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/46xf4h0w(v=vs.100)#using-the-document-outline-window-for-silverlight-and-wpf).</span></span>

8. <span data-ttu-id="f3fb3-137">W **właściwości** okna, ustaw wartość <xref:System.Windows.Forms.Control.Padding%2A> właściwość `10, 10, 10, 10`.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-137">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Padding%2A> property to `10, 10, 10, 10`.</span></span>

     <span data-ttu-id="f3fb3-138">Zarówno <xref:System.Windows.Forms.Integration.ElementHost> formanty są dopasowane do do nowego układu.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-138">Both <xref:System.Windows.Forms.Integration.ElementHost> controls are resized to fit into the new layout.</span></span>

## <a name="using-snaplines-to-align-wpf-controls"></a><span data-ttu-id="f3fb3-139">Aby wyrównać formanty WPF za pomocą linii przyciągania</span><span class="sxs-lookup"><span data-stu-id="f3fb3-139">Using Snaplines to Align WPF Controls</span></span>
 <span data-ttu-id="f3fb3-140">Linii przyciągania umożliwiają łatwe wyrównanie kontrolek w formularzu.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-140">Snaplines enable easy alignment of controls on a form.</span></span> <span data-ttu-id="f3fb3-141">Za pomocą linii przyciągania do wyrównania Twoich kontrolek WPF.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-141">You can use snaplines to align your WPF controls as well.</span></span> <span data-ttu-id="f3fb3-142">Aby uzyskać więcej informacji, zobacz [instruktażu: Rozmieszczanie formantów Windows Forms za pomocą linii przyciągania](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="f3fb3-142">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>

#### <a name="to-use-snaplines-to-align-wpf-controls"></a><span data-ttu-id="f3fb3-143">Wyrównaj WPF za pomocą linii przyciągania kontrolki</span><span class="sxs-lookup"><span data-stu-id="f3fb3-143">To use snaplines to align WPF controls</span></span>

1. <span data-ttu-id="f3fb3-144">Z **przybornika**, przeciągnij wystąpienie `UserControl1` na formularz i umieść go w miejsce poniżej <xref:System.Windows.Forms.TableLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-144">From the **Toolbox**, drag an instance of `UserControl1` onto the form and place it in the space beneath the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

     <span data-ttu-id="f3fb3-145">Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-145">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost3`.</span></span>

2. <span data-ttu-id="f3fb3-146">Za pomocą linii przyciągania, Wyrównaj do lewej krawędzi `elementHost3` lewej krawędzi <xref:System.Windows.Forms.TableLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-146">Using snaplines, align the left edge of `elementHost3` with the left edge of <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

3. <span data-ttu-id="f3fb3-147">Za pomocą linii przyciągania, rozmiar `elementHost3` mają taką samą szerokość jako <xref:System.Windows.Forms.TableLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-147">Using snaplines, size `elementHost3` to the same width as the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

4. <span data-ttu-id="f3fb3-148">Przenieś `elementHost3` kierunku <xref:System.Windows.Forms.TableLayoutPanel> kontrolować aż snapline — Centrum pojawi się między formantami.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-148">Move `elementHost3` toward the <xref:System.Windows.Forms.TableLayoutPanel> control until a center snapline appears between the controls.</span></span>

5. <span data-ttu-id="f3fb3-149">W **właściwości** okna, ustaw wartość właściwości marginesów `20, 20, 20, 20`.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-149">In the **Properties** window, set the value of the Margin property to `20, 20, 20, 20`.</span></span>

6. <span data-ttu-id="f3fb3-150">Przenieś `elementHost3` opuszczenie <xref:System.Windows.Forms.TableLayoutPanel> kontrolować aż snapline — Centrum pojawi się ponownie.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-150">Move the `elementHost3` away from the <xref:System.Windows.Forms.TableLayoutPanel> control until the center snapline appears again.</span></span> <span data-ttu-id="f3fb3-151">Snapline — Centrum wskazuje teraz margines 20.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-151">The center snapline now indicates a margin of 20.</span></span>

7. <span data-ttu-id="f3fb3-152">Przenieś `elementHost3` z prawej strony, do momentu jego lewej krawędzi jest wyrównywany do lewej krawędzi `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-152">Move `elementHost3` to the right, until its left edge aligns with the left edge of `elementHost1`.</span></span>

8. <span data-ttu-id="f3fb3-153">Zmień szerokość `elementHost3` do momentu jego prawej krawędzi wyrównuje do prawej krawędzi `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-153">Change the width of `elementHost3` until its right edge aligns with the right edge of `elementHost2`.</span></span>

## <a name="anchoring-and-docking-wpf-controls"></a><span data-ttu-id="f3fb3-154">Zakotwiczanie i dokowanie kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="f3fb3-154">Anchoring and Docking WPF Controls</span></span>
 <span data-ttu-id="f3fb3-155">Kontrolki WPF w serwisie formularza ma, które ten sam Zakotwiczanie i dokowanie zachowanie, jak inne kontrolki Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-155">A WPF control hosted on a form has the same anchoring and docking behavior as other Windows Forms controls.</span></span>

#### <a name="to-anchor-and-dock-wpf-controls"></a><span data-ttu-id="f3fb3-156">Aby zakotwiczenie i dokowanie kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="f3fb3-156">To anchor and dock WPF controls</span></span>

1. <span data-ttu-id="f3fb3-157">Wybierz `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-157">Select `elementHost1`.</span></span>

2. <span data-ttu-id="f3fb3-158">W **właściwości** oknie <xref:System.Windows.Forms.Control.Anchor%2A> właściwości **górnej, dolnej, lewe, prawe**.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-158">In the **Properties** window, set the <xref:System.Windows.Forms.Control.Anchor%2A> property to **Top, Bottom, Left, Right**.</span></span>

3. <span data-ttu-id="f3fb3-159">Zmień rozmiar <xref:System.Windows.Forms.TableLayoutPanel> kontrolki o większym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-159">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger size.</span></span>

     <span data-ttu-id="f3fb3-160">`elementHost1` Kontrolować zmiany rozmiaru w celu wypełnienia komórki.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-160">The `elementHost1` control resizes to fill the cell.</span></span>

4. <span data-ttu-id="f3fb3-161">Wybierz `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-161">Select `elementHost2`.</span></span>

5. <span data-ttu-id="f3fb3-162">W **właściwości** okna, ustaw wartość <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-162">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

     <span data-ttu-id="f3fb3-163">`elementHost2` Kontrolować zmiany rozmiaru w celu wypełnienia komórki.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-163">The `elementHost2` control resizes to fill the cell.</span></span>

6. <span data-ttu-id="f3fb3-164">Wybierz <xref:System.Windows.Forms.TableLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-164">Select the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>

7. <span data-ttu-id="f3fb3-165">Ustaw wartość jego <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Top>.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-165">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Top>.</span></span>

8. <span data-ttu-id="f3fb3-166">Wybierz `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-166">Select `elementHost3`.</span></span>

9. <span data-ttu-id="f3fb3-167">Ustaw wartość jego <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-167">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

     <span data-ttu-id="f3fb3-168">`elementHost3` Kontrolować zmiany rozmiaru w celu wypełnienia pozostałego miejsca w formularzu.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-168">The `elementHost3` control resizes to fill the remaining space on the form.</span></span>

10. <span data-ttu-id="f3fb3-169">Zmień rozmiar formularza.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-169">Resize the form.</span></span>

     <span data-ttu-id="f3fb3-170">Wszystkie trzy <xref:System.Windows.Forms.Integration.ElementHost> odpowiednio zmień rozmiar kontrolki.</span><span class="sxs-lookup"><span data-stu-id="f3fb3-170">All three <xref:System.Windows.Forms.Integration.ElementHost> controls resize appropriately.</span></span>

     <span data-ttu-id="f3fb3-171">Aby uzyskać więcej informacji, zobacz [jak: Zakotwiczenie i dokowanie formantów podrzędnych w formancie TableLayoutPanel](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span><span class="sxs-lookup"><span data-stu-id="f3fb3-171">For more information, see [How to: Anchor and Dock Child Controls in a TableLayoutPanel Control](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f3fb3-172">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3fb3-172">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="f3fb3-173">Instrukcje: Zakotwiczenie i dokowanie formantów podrzędnych w formancie TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f3fb3-173">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="f3fb3-174">Instrukcje: Wyrównywanie formantu z krawędziami formularzy w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="f3fb3-174">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)
- [<span data-ttu-id="f3fb3-175">Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania</span><span class="sxs-lookup"><span data-stu-id="f3fb3-175">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="f3fb3-176">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="f3fb3-176">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="f3fb3-177">Korzystanie z kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="f3fb3-177">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="f3fb3-178">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f3fb3-178">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
