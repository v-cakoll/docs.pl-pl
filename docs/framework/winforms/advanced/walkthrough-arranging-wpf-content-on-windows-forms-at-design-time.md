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
ms.openlocfilehash: 1466591a06e9e7ca61f94683e037566f8d0cb31a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509778"
---
# <a name="walkthrough-arranging-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="0e2ff-102">Wskazówki: rozmieszczanie zawartości WPF na formularzach systemu Windows w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="0e2ff-102">Walkthrough: Arranging WPF Content on Windows Forms at Design Time</span></span>
<span data-ttu-id="0e2ff-103">W tym instruktażu przedstawiono sposób korzystania z funkcji układu formularzy Windows, takich jak Zakotwiczanie i linii przyciągania, aby rozmieścić formanty Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="0e2ff-103">This walkthrough shows you how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation (WPF) controls.</span></span>  
  
 <span data-ttu-id="0e2ff-104">W tym przewodniku należy wykonać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="0e2ff-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="0e2ff-105">Utwórz projekt.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-105">Create the project.</span></span>  
  
-   <span data-ttu-id="0e2ff-106">Tworzenie formantu WPF.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-106">Create the WPF control.</span></span>  
  
-   <span data-ttu-id="0e2ff-107">Host formantów WPF w panelu układu.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-107">Host WPF controls in a layout panel.</span></span>  
  
-   <span data-ttu-id="0e2ff-108">Linii przyciągania użycia do wyrównania kontrolek WPF.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-108">Use snaplines to align WPF controls.</span></span>  
  
-   <span data-ttu-id="0e2ff-109">Zakotwiczenie i dokowanie kontrolek WPF.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-109">Anchor and dock WPF controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0e2ff-110">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-110">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="0e2ff-111">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-111">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="0e2ff-112">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="0e2ff-112">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0e2ff-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="0e2ff-113">Prerequisites</span></span>  
 <span data-ttu-id="0e2ff-114">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="0e2ff-114">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="0e2ff-115">.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-115">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="0e2ff-116">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="0e2ff-116">Creating the Project</span></span>  
 <span data-ttu-id="0e2ff-117">Pierwszym krokiem jest utworzenie projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-117">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0e2ff-118">Gdy hosting zawartości WPF, obsługiwane są tylko C# i projektach języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-118">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="0e2ff-119">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="0e2ff-119">To create the project</span></span>  
  
-   <span data-ttu-id="0e2ff-120">Tworzenie nowego projektu aplikacji formularzy Windows w języku Visual Basic lub Visual C# o nazwie `ArrangeElementHost`.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-120">Create a new Windows Forms Application project in Visual Basic or Visual C# named `ArrangeElementHost`.</span></span>  
  
## <a name="creating-the-wpf-control"></a><span data-ttu-id="0e2ff-121">Tworzenie kontrolki WPF</span><span class="sxs-lookup"><span data-stu-id="0e2ff-121">Creating the WPF Control</span></span>  
 <span data-ttu-id="0e2ff-122">Po dodaniu kontrolki WPF do projektu, można rozmieścić je na formularzu.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-122">After you add a WPF control to the project, you can arrange it on the form.</span></span>  
  
#### <a name="to-create-wpf-controls"></a><span data-ttu-id="0e2ff-123">Aby utworzyć formanty WPF</span><span class="sxs-lookup"><span data-stu-id="0e2ff-123">To create WPF controls</span></span>  
  
1.  <span data-ttu-id="0e2ff-124">Dodaj nowe WPF <xref:System.Windows.Controls.UserControl> do projektu.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-124">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="0e2ff-125">Użyj domyślnej nazwy dla kontrolek typu `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-125">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="0e2ff-126">Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie nowego WPF zawartości na formularzach Windows Forms w czasie projektowania](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="0e2ff-126">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="0e2ff-127">W widoku Projekt, upewnij się, że `UserControl1` jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-127">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="0e2ff-128">Aby uzyskać więcej informacji, zobacz [jak: Select i Przesuń elementy na powierzchni projektowej](https://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span><span class="sxs-lookup"><span data-stu-id="0e2ff-128">For more information, see [How to: Select and Move Elements on the Design Surface](https://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="0e2ff-129">W **właściwości** okna, ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości `200`.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-129">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="0e2ff-130">Ustaw wartość <xref:System.Windows.Controls.Control.Background%2A> właściwość `Blue`.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-130">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>  
  
5.  <span data-ttu-id="0e2ff-131">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-131">Build the project.</span></span>  
  
## <a name="hosting-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="0e2ff-132">Hosting kontrolek WPF w panelu układu</span><span class="sxs-lookup"><span data-stu-id="0e2ff-132">Hosting WPF Controls in a Layout Panel</span></span>  
 <span data-ttu-id="0e2ff-133">Umożliwia kontrolek WPF w panele układów w taki sam sposób, jak używać innych kontrolek Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-133">You can use WPF controls in layout panels in the same way you use other Windows Forms controls.</span></span>  
  
#### <a name="to-host-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="0e2ff-134">Host formantów WPF w panelu układu</span><span class="sxs-lookup"><span data-stu-id="0e2ff-134">To host WPF controls in a layout panel</span></span>  
  
1.  <span data-ttu-id="0e2ff-135">Otwórz `Form1` w programie Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-135">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="0e2ff-136">W **przybornika**, przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> formant na formularzu.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-136">In the **Toolbox**, drag a <xref:System.Windows.Forms.TableLayoutPanel> control onto the form.</span></span>  
  
3.  <span data-ttu-id="0e2ff-137">Na <xref:System.Windows.Forms.TableLayoutPanel> kontrolki panelu tagi inteligentne, wybierz **Usuń ostatni wiersz**.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-137">On the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag panel, select **Remove Last Row**.</span></span>  
  
4.  <span data-ttu-id="0e2ff-138">Zmień rozmiar <xref:System.Windows.Forms.TableLayoutPanel> kontrolki większych szerokość i wysokość.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-138">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger width and height.</span></span>  
  
5.  <span data-ttu-id="0e2ff-139">W **przybornika**, kliknij dwukrotnie `UserControl1` do utworzenia wystąpienia `UserControl1` w pierwszej komórki z <xref:System.Windows.Forms.TableLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-139">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` in the first cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
     <span data-ttu-id="0e2ff-140">Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-140">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
6.  <span data-ttu-id="0e2ff-141">W **przybornika**, kliknij dwukrotnie `UserControl1` Aby utworzyć inną instancję w drugiej komórce <xref:System.Windows.Forms.TableLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-141">In the **Toolbox**, double-click `UserControl1` to create another instance in the second cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
7.  <span data-ttu-id="0e2ff-142">W **konspekt dokumentu** wybierz `tableLayoutPanel1`.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-142">In the **Document Outline** window, select `tableLayoutPanel1`.</span></span> <span data-ttu-id="0e2ff-143">Aby uzyskać więcej informacji, zobacz [okno konspektu dokumentu](https://msdn.microsoft.com/library/9054f2bc-f6f8-4242-9fe0-be71089b12f8).</span><span class="sxs-lookup"><span data-stu-id="0e2ff-143">For more information, see [Document Outline Window](https://msdn.microsoft.com/library/9054f2bc-f6f8-4242-9fe0-be71089b12f8).</span></span>  
  
8.  <span data-ttu-id="0e2ff-144">W **właściwości** okna, ustaw wartość <xref:System.Windows.Forms.Control.Padding%2A> właściwość `10, 10, 10, 10`.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-144">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Padding%2A> property to `10, 10, 10, 10`.</span></span>  
  
     <span data-ttu-id="0e2ff-145">Zarówno <xref:System.Windows.Forms.Integration.ElementHost> formanty są dopasowane do do nowego układu.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-145">Both <xref:System.Windows.Forms.Integration.ElementHost> controls are resized to fit into the new layout.</span></span>  
  
## <a name="using-snaplines-to-align-wpf-controls"></a><span data-ttu-id="0e2ff-146">Aby wyrównać formanty WPF za pomocą linii przyciągania</span><span class="sxs-lookup"><span data-stu-id="0e2ff-146">Using Snaplines to Align WPF Controls</span></span>  
 <span data-ttu-id="0e2ff-147">Linii przyciągania umożliwiają łatwe wyrównanie kontrolek w formularzu.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-147">Snaplines enable easy alignment of controls on a form.</span></span> <span data-ttu-id="0e2ff-148">Za pomocą linii przyciągania do wyrównania Twoich kontrolek WPF.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-148">You can use snaplines to align your WPF controls as well.</span></span> <span data-ttu-id="0e2ff-149">Aby uzyskać więcej informacji, zobacz [wskazówki: rozmieszczanie formantów Windows Forms za pomocą linii przyciągania](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="0e2ff-149">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>  
  
#### <a name="to-use-snaplines-to-align-wpf-controls"></a><span data-ttu-id="0e2ff-150">Wyrównaj WPF za pomocą linii przyciągania kontrolki</span><span class="sxs-lookup"><span data-stu-id="0e2ff-150">To use snaplines to align WPF controls</span></span>  
  
1.  <span data-ttu-id="0e2ff-151">Z **przybornika**, przeciągnij wystąpienie `UserControl1` na formularz i umieść go w miejsce poniżej <xref:System.Windows.Forms.TableLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-151">From the **Toolbox**, drag an instance of `UserControl1` onto the form and place it in the space beneath the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
     <span data-ttu-id="0e2ff-152">Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-152">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost3`.</span></span>  
  
2.  <span data-ttu-id="0e2ff-153">Za pomocą linii przyciągania, Wyrównaj do lewej krawędzi `elementHost3` lewej krawędzi <xref:System.Windows.Forms.TableLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-153">Using snaplines, align the left edge of `elementHost3` with the left edge of <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
3.  <span data-ttu-id="0e2ff-154">Za pomocą linii przyciągania, rozmiar `elementHost3` mają taką samą szerokość jako <xref:System.Windows.Forms.TableLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-154">Using snaplines, size `elementHost3` to the same width as the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
4.  <span data-ttu-id="0e2ff-155">Przenieś `elementHost3` kierunku <xref:System.Windows.Forms.TableLayoutPanel> kontrolować aż snapline — Centrum pojawi się między formantami.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-155">Move `elementHost3` toward the <xref:System.Windows.Forms.TableLayoutPanel> control until a center snapline appears between the controls.</span></span>  
  
5.  <span data-ttu-id="0e2ff-156">W **właściwości** okna, ustaw wartość właściwości marginesów `20, 20, 20, 20`.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-156">In the **Properties** window, set the value of the Margin property to `20, 20, 20, 20`.</span></span>  
  
6.  <span data-ttu-id="0e2ff-157">Przenieś `elementHost3` opuszczenie <xref:System.Windows.Forms.TableLayoutPanel> kontrolować aż snapline — Centrum pojawi się ponownie.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-157">Move the `elementHost3` away from the <xref:System.Windows.Forms.TableLayoutPanel> control until the center snapline appears again.</span></span> <span data-ttu-id="0e2ff-158">Snapline — Centrum wskazuje teraz margines 20.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-158">The center snapline now indicates a margin of 20.</span></span>  
  
7.  <span data-ttu-id="0e2ff-159">Przenieś `elementHost3` z prawej strony, do momentu jego lewej krawędzi jest wyrównywany do lewej krawędzi `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-159">Move `elementHost3` to the right, until its left edge aligns with the left edge of `elementHost1`.</span></span>  
  
8.  <span data-ttu-id="0e2ff-160">Zmień szerokość `elementHost3` do momentu jego prawej krawędzi wyrównuje do prawej krawędzi `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-160">Change the width of `elementHost3` until its right edge aligns with the right edge of `elementHost2`.</span></span>  
  
## <a name="anchoring-and-docking-wpf-controls"></a><span data-ttu-id="0e2ff-161">Zakotwiczanie i dokowanie kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="0e2ff-161">Anchoring and Docking WPF Controls</span></span>  
 <span data-ttu-id="0e2ff-162">Kontrolki WPF w serwisie formularza ma, które ten sam Zakotwiczanie i dokowanie zachowanie, jak inne kontrolki Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-162">A WPF control hosted on a form has the same anchoring and docking behavior as other Windows Forms controls.</span></span>  
  
#### <a name="to-anchor-and-dock-wpf-controls"></a><span data-ttu-id="0e2ff-163">Aby zakotwiczenie i dokowanie kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="0e2ff-163">To anchor and dock WPF controls</span></span>  
  
1.  <span data-ttu-id="0e2ff-164">Wybierz `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-164">Select `elementHost1`.</span></span>  
  
2.  <span data-ttu-id="0e2ff-165">W **właściwości** oknie <xref:System.Windows.Forms.Control.Anchor%2A> właściwości **górnej, dolnej, lewe, prawe**.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-165">In the **Properties** window, set the <xref:System.Windows.Forms.Control.Anchor%2A> property to **Top, Bottom, Left, Right**.</span></span>  
  
3.  <span data-ttu-id="0e2ff-166">Zmień rozmiar <xref:System.Windows.Forms.TableLayoutPanel> kontrolki o większym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-166">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger size.</span></span>  
  
     <span data-ttu-id="0e2ff-167">`elementHost1` Kontrolować zmiany rozmiaru w celu wypełnienia komórki.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-167">The `elementHost1` control resizes to fill the cell.</span></span>  
  
4.  <span data-ttu-id="0e2ff-168">Wybierz `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-168">Select `elementHost2`.</span></span>  
  
5.  <span data-ttu-id="0e2ff-169">W **właściwości** okna, ustaw wartość <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-169">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
     <span data-ttu-id="0e2ff-170">`elementHost2` Kontrolować zmiany rozmiaru w celu wypełnienia komórki.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-170">The `elementHost2` control resizes to fill the cell.</span></span>  
  
6.  <span data-ttu-id="0e2ff-171">Wybierz <xref:System.Windows.Forms.TableLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-171">Select the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
7.  <span data-ttu-id="0e2ff-172">Ustaw wartość jego <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Top>.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-172">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Top>.</span></span>  
  
8.  <span data-ttu-id="0e2ff-173">Wybierz `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-173">Select `elementHost3`.</span></span>  
  
9. <span data-ttu-id="0e2ff-174">Ustaw wartość jego <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-174">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
     <span data-ttu-id="0e2ff-175">`elementHost3` Kontrolować zmiany rozmiaru w celu wypełnienia pozostałego miejsca w formularzu.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-175">The `elementHost3` control resizes to fill the remaining space on the form.</span></span>  
  
10. <span data-ttu-id="0e2ff-176">Zmień rozmiar formularza.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-176">Resize the form.</span></span>  
  
     <span data-ttu-id="0e2ff-177">Wszystkie trzy <xref:System.Windows.Forms.Integration.ElementHost> odpowiednio zmień rozmiar kontrolki.</span><span class="sxs-lookup"><span data-stu-id="0e2ff-177">All three <xref:System.Windows.Forms.Integration.ElementHost> controls resize appropriately.</span></span>  
  
     <span data-ttu-id="0e2ff-178">Aby uzyskać więcej informacji, zobacz [porady: zakotwiczenie i Dock formantów podrzędnych w formancie TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span><span class="sxs-lookup"><span data-stu-id="0e2ff-178">For more information, see [How to: Anchor and Dock Child Controls in a TableLayoutPanel Control](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e2ff-179">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0e2ff-179">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="0e2ff-180">Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="0e2ff-180">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="0e2ff-181">Instrukcje: wyrównywanie kontrolki z krawędziami formularzy w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="0e2ff-181">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 [<span data-ttu-id="0e2ff-182">Przewodnik: rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania</span><span class="sxs-lookup"><span data-stu-id="0e2ff-182">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="0e2ff-183">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="0e2ff-183">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="0e2ff-184">Korzystanie z kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="0e2ff-184">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="0e2ff-185">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0e2ff-185">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
