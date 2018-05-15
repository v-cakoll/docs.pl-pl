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
ms.openlocfilehash: 373a7f977a9dad59cd40fd29fdd39c8fc6996ad0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-arranging-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="8b31c-102">Wskazówki: rozmieszczanie zawartości WPF na formularzach systemu Windows w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="8b31c-102">Walkthrough: Arranging WPF Content on Windows Forms at Design Time</span></span>
<span data-ttu-id="8b31c-103">W tym przewodniku przedstawiono możliwości korzystania z funkcji układ formularzy systemu Windows, takich jak Zakotwiczanie i linie przyciągania, ułożyć kontrolki Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="8b31c-103">This walkthrough shows you how to use the Windows Forms layout features, such as anchoring and snaplines, to arrange Windows Presentation Foundation (WPF) controls.</span></span>  
  
 <span data-ttu-id="8b31c-104">W tym przewodniku należy wykonać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="8b31c-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="8b31c-105">Tworzenie projektu.</span><span class="sxs-lookup"><span data-stu-id="8b31c-105">Create the project.</span></span>  
  
-   <span data-ttu-id="8b31c-106">Tworzenie formantu WPF.</span><span class="sxs-lookup"><span data-stu-id="8b31c-106">Create the WPF control.</span></span>  
  
-   <span data-ttu-id="8b31c-107">Host formantów WPF w panelu układu.</span><span class="sxs-lookup"><span data-stu-id="8b31c-107">Host WPF controls in a layout panel.</span></span>  
  
-   <span data-ttu-id="8b31c-108">Linie przyciągania Użyj, aby były wyrównane formantów WPF.</span><span class="sxs-lookup"><span data-stu-id="8b31c-108">Use snaplines to align WPF controls.</span></span>  
  
-   <span data-ttu-id="8b31c-109">Zakotwiczenie i dokowanie formantów WPF.</span><span class="sxs-lookup"><span data-stu-id="8b31c-109">Anchor and dock WPF controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b31c-110">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="8b31c-110">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="8b31c-111">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="8b31c-111">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="8b31c-112">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="8b31c-112">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8b31c-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="8b31c-113">Prerequisites</span></span>  
 <span data-ttu-id="8b31c-114">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="8b31c-114">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="8b31c-115">.</span><span class="sxs-lookup"><span data-stu-id="8b31c-115">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="8b31c-116">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="8b31c-116">Creating the Project</span></span>  
 <span data-ttu-id="8b31c-117">Pierwszym krokiem jest utworzenie projektu formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8b31c-117">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b31c-118">Jeżeli hostowanie zawartości WPF, obsługiwane są tylko C# i Visual Basic, projekty.</span><span class="sxs-lookup"><span data-stu-id="8b31c-118">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="8b31c-119">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="8b31c-119">To create the project</span></span>  
  
-   <span data-ttu-id="8b31c-120">Utwórz nowy projekt aplikacji formularzy systemu Windows w języku Visual Basic lub Visual C# o nazwie `ArrangeElementHost`.</span><span class="sxs-lookup"><span data-stu-id="8b31c-120">Create a new Windows Forms Application project in Visual Basic or Visual C# named `ArrangeElementHost`.</span></span>  
  
## <a name="creating-the-wpf-control"></a><span data-ttu-id="8b31c-121">Tworzenie formantu WPF</span><span class="sxs-lookup"><span data-stu-id="8b31c-121">Creating the WPF Control</span></span>  
 <span data-ttu-id="8b31c-122">Po dodaniu formantu WPF do projektu można rozmieścić go w formularzu.</span><span class="sxs-lookup"><span data-stu-id="8b31c-122">After you add a WPF control to the project, you can arrange it on the form.</span></span>  
  
#### <a name="to-create-wpf-controls"></a><span data-ttu-id="8b31c-123">Aby utworzyć formantów WPF</span><span class="sxs-lookup"><span data-stu-id="8b31c-123">To create WPF controls</span></span>  
  
1.  <span data-ttu-id="8b31c-124">Dodaj nowy WPF <xref:System.Windows.Controls.UserControl> do projektu.</span><span class="sxs-lookup"><span data-stu-id="8b31c-124">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="8b31c-125">Użyj domyślnej nazwy dla typu formantu `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="8b31c-125">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="8b31c-126">Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie nowego WPF zawartości w formularzach systemu Windows w czasie projektowania](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="8b31c-126">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="8b31c-127">W widoku Projekt, upewnij się, że `UserControl1` jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="8b31c-127">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="8b31c-128">Aby uzyskać więcej informacji, zobacz [porady: Wybierz i Przenieś elementy na powierzchnię projektu](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span><span class="sxs-lookup"><span data-stu-id="8b31c-128">For more information, see [How to: Select and Move Elements on the Design Surface](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="8b31c-129">W **właściwości** okna, ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości `200`.</span><span class="sxs-lookup"><span data-stu-id="8b31c-129">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="8b31c-130">Ustaw wartość <xref:System.Windows.Controls.Control.Background%2A> właściwości `Blue`.</span><span class="sxs-lookup"><span data-stu-id="8b31c-130">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>  
  
5.  <span data-ttu-id="8b31c-131">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="8b31c-131">Build the project.</span></span>  
  
## <a name="hosting-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="8b31c-132">Hosting formantów WPF w panelu układu</span><span class="sxs-lookup"><span data-stu-id="8b31c-132">Hosting WPF Controls in a Layout Panel</span></span>  
 <span data-ttu-id="8b31c-133">Używając formantów WPF w panele układu w taki sam sposób, jak używać inne formanty formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8b31c-133">You can use WPF controls in layout panels in the same way you use other Windows Forms controls.</span></span>  
  
#### <a name="to-host-wpf-controls-in-a-layout-panel"></a><span data-ttu-id="8b31c-134">Na hoście formantów WPF w panelu układu</span><span class="sxs-lookup"><span data-stu-id="8b31c-134">To host WPF controls in a layout panel</span></span>  
  
1.  <span data-ttu-id="8b31c-135">Otwórz `Form1` w narzędziu Projektant dla formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8b31c-135">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="8b31c-136">W **przybornika**, przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> sterowania do formularza.</span><span class="sxs-lookup"><span data-stu-id="8b31c-136">In the **Toolbox**, drag a <xref:System.Windows.Forms.TableLayoutPanel> control onto the form.</span></span>  
  
3.  <span data-ttu-id="8b31c-137">Na <xref:System.Windows.Forms.TableLayoutPanel> kontrolki panelu tagów inteligentnych, wybierz opcję **Usuń ostatni wiersz**.</span><span class="sxs-lookup"><span data-stu-id="8b31c-137">On the <xref:System.Windows.Forms.TableLayoutPanel> control's smart tag panel, select **Remove Last Row**.</span></span>  
  
4.  <span data-ttu-id="8b31c-138">Zmień rozmiar <xref:System.Windows.Forms.TableLayoutPanel> kontroli większych szerokości i wysokości.</span><span class="sxs-lookup"><span data-stu-id="8b31c-138">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger width and height.</span></span>  
  
5.  <span data-ttu-id="8b31c-139">W **przybornika**, kliknij dwukrotnie `UserControl1` można utworzyć wystąpienia `UserControl1` w komórce pierwszy <xref:System.Windows.Forms.TableLayoutPanel> formantu.</span><span class="sxs-lookup"><span data-stu-id="8b31c-139">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` in the first cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
     <span data-ttu-id="8b31c-140">Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="8b31c-140">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
6.  <span data-ttu-id="8b31c-141">W **przybornika**, kliknij dwukrotnie `UserControl1` Aby utworzyć inne wystąpienie w komórce drugi <xref:System.Windows.Forms.TableLayoutPanel> formantu.</span><span class="sxs-lookup"><span data-stu-id="8b31c-141">In the **Toolbox**, double-click `UserControl1` to create another instance in the second cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
7.  <span data-ttu-id="8b31c-142">W **konspekt dokumentu** wybierz `tableLayoutPanel1`.</span><span class="sxs-lookup"><span data-stu-id="8b31c-142">In the **Document Outline** window, select `tableLayoutPanel1`.</span></span> <span data-ttu-id="8b31c-143">Aby uzyskać więcej informacji, zobacz [okno konspektu dokumentu](http://msdn.microsoft.com/library/9054f2bc-f6f8-4242-9fe0-be71089b12f8).</span><span class="sxs-lookup"><span data-stu-id="8b31c-143">For more information, see [Document Outline Window](http://msdn.microsoft.com/library/9054f2bc-f6f8-4242-9fe0-be71089b12f8).</span></span>  
  
8.  <span data-ttu-id="8b31c-144">W **właściwości** okna, ustaw wartość <xref:System.Windows.Forms.Control.Padding%2A> właściwości `10, 10, 10, 10`.</span><span class="sxs-lookup"><span data-stu-id="8b31c-144">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Padding%2A> property to `10, 10, 10, 10`.</span></span>  
  
     <span data-ttu-id="8b31c-145">Zarówno <xref:System.Windows.Forms.Integration.ElementHost> formanty są dopasowane do do nowego układu.</span><span class="sxs-lookup"><span data-stu-id="8b31c-145">Both <xref:System.Windows.Forms.Integration.ElementHost> controls are resized to fit into the new layout.</span></span>  
  
## <a name="using-snaplines-to-align-wpf-controls"></a><span data-ttu-id="8b31c-146">Aby wyrównać formantów WPF za pomocą linii przyciągania</span><span class="sxs-lookup"><span data-stu-id="8b31c-146">Using Snaplines to Align WPF Controls</span></span>  
 <span data-ttu-id="8b31c-147">Linie przyciągania umożliwiają łatwe wyrównanie kontrolek w formularzu.</span><span class="sxs-lookup"><span data-stu-id="8b31c-147">Snaplines enable easy alignment of controls on a form.</span></span> <span data-ttu-id="8b31c-148">Linie przyciągania umożliwia wyrównywanie Twoich formantów WPF.</span><span class="sxs-lookup"><span data-stu-id="8b31c-148">You can use snaplines to align your WPF controls as well.</span></span> <span data-ttu-id="8b31c-149">Aby uzyskać więcej informacji, zobacz [wskazówki: rozmieszczanie formantów na formularzach systemu Windows przy użyciu linie przyciągania](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span><span class="sxs-lookup"><span data-stu-id="8b31c-149">For more information, see [Walkthrough: Arranging Controls on Windows Forms Using Snaplines](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).</span></span>  
  
#### <a name="to-use-snaplines-to-align-wpf-controls"></a><span data-ttu-id="8b31c-150">Na potrzeby Dopasuj WPF linie przyciągania kontrolki</span><span class="sxs-lookup"><span data-stu-id="8b31c-150">To use snaplines to align WPF controls</span></span>  
  
1.  <span data-ttu-id="8b31c-151">Z **przybornika**, przeciągnij wystąpienia `UserControl1` na formularz i umieść go w obszarze poniżej <xref:System.Windows.Forms.TableLayoutPanel> formantu.</span><span class="sxs-lookup"><span data-stu-id="8b31c-151">From the **Toolbox**, drag an instance of `UserControl1` onto the form and place it in the space beneath the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
     <span data-ttu-id="8b31c-152">Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="8b31c-152">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost3`.</span></span>  
  
2.  <span data-ttu-id="8b31c-153">Za pomocą linii przyciągania, wyrównanie do lewej krawędzi `elementHost3` lewej krawędzi <xref:System.Windows.Forms.TableLayoutPanel> formantu.</span><span class="sxs-lookup"><span data-stu-id="8b31c-153">Using snaplines, align the left edge of `elementHost3` with the left edge of <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
3.  <span data-ttu-id="8b31c-154">Za pomocą linii przyciągania, rozmiar `elementHost3` do tej samej szerokości jako <xref:System.Windows.Forms.TableLayoutPanel> formantu.</span><span class="sxs-lookup"><span data-stu-id="8b31c-154">Using snaplines, size `elementHost3` to the same width as the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
4.  <span data-ttu-id="8b31c-155">Przenieś `elementHost3` kierunku <xref:System.Windows.Forms.TableLayoutPanel> kontrolować aż snapline — center pojawi się między formantami.</span><span class="sxs-lookup"><span data-stu-id="8b31c-155">Move `elementHost3` toward the <xref:System.Windows.Forms.TableLayoutPanel> control until a center snapline appears between the controls.</span></span>  
  
5.  <span data-ttu-id="8b31c-156">W **właściwości** okna, ustaw wartość właściwości margines `20, 20, 20, 20`.</span><span class="sxs-lookup"><span data-stu-id="8b31c-156">In the **Properties** window, set the value of the Margin property to `20, 20, 20, 20`.</span></span>  
  
6.  <span data-ttu-id="8b31c-157">Przenieś `elementHost3` od <xref:System.Windows.Forms.TableLayoutPanel> kontrolować aż snapline — center pojawi się ponownie.</span><span class="sxs-lookup"><span data-stu-id="8b31c-157">Move the `elementHost3` away from the <xref:System.Windows.Forms.TableLayoutPanel> control until the center snapline appears again.</span></span> <span data-ttu-id="8b31c-158">Snapline — center wskazuje teraz margines 20.</span><span class="sxs-lookup"><span data-stu-id="8b31c-158">The center snapline now indicates a margin of 20.</span></span>  
  
7.  <span data-ttu-id="8b31c-159">Przenieś `elementHost3` z prawej strony, do momentu jego lewej krawędzi jest wyrównywany do lewej krawędzi `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="8b31c-159">Move `elementHost3` to the right, until its left edge aligns with the left edge of `elementHost1`.</span></span>  
  
8.  <span data-ttu-id="8b31c-160">Zmień szerokość `elementHost3` do momentu jego prawej krawędzi wyrównuje do prawej krawędzi `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="8b31c-160">Change the width of `elementHost3` until its right edge aligns with the right edge of `elementHost2`.</span></span>  
  
## <a name="anchoring-and-docking-wpf-controls"></a><span data-ttu-id="8b31c-161">Zakotwiczanie i dokowanie formantów WPF</span><span class="sxs-lookup"><span data-stu-id="8b31c-161">Anchoring and Docking WPF Controls</span></span>  
 <span data-ttu-id="8b31c-162">Formant WPF hostowanych na formularzu ma tej samej Zakotwiczanie i dokowanie zachowanie jako inne formanty formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8b31c-162">A WPF control hosted on a form has the same anchoring and docking behavior as other Windows Forms controls.</span></span>  
  
#### <a name="to-anchor-and-dock-wpf-controls"></a><span data-ttu-id="8b31c-163">Aby zakotwiczenie i dokowanie formantów WPF</span><span class="sxs-lookup"><span data-stu-id="8b31c-163">To anchor and dock WPF controls</span></span>  
  
1.  <span data-ttu-id="8b31c-164">Wybierz `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="8b31c-164">Select `elementHost1`.</span></span>  
  
2.  <span data-ttu-id="8b31c-165">W **właściwości** ustaw <xref:System.Windows.Forms.Control.Anchor%2A> właściwości **górnej i dolnej lewe, prawe**.</span><span class="sxs-lookup"><span data-stu-id="8b31c-165">In the **Properties** window, set the <xref:System.Windows.Forms.Control.Anchor%2A> property to **Top, Bottom, Left, Right**.</span></span>  
  
3.  <span data-ttu-id="8b31c-166">Zmień rozmiar <xref:System.Windows.Forms.TableLayoutPanel> większy rozmiar formantu.</span><span class="sxs-lookup"><span data-stu-id="8b31c-166">Resize the <xref:System.Windows.Forms.TableLayoutPanel> control to a larger size.</span></span>  
  
     <span data-ttu-id="8b31c-167">`elementHost1` Kontrolować zmienia rozmiar do wypełnienia komórki.</span><span class="sxs-lookup"><span data-stu-id="8b31c-167">The `elementHost1` control resizes to fill the cell.</span></span>  
  
4.  <span data-ttu-id="8b31c-168">Wybierz `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="8b31c-168">Select `elementHost2`.</span></span>  
  
5.  <span data-ttu-id="8b31c-169">W **właściwości** okna, ustaw wartość <xref:System.Windows.Forms.Control.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="8b31c-169">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
     <span data-ttu-id="8b31c-170">`elementHost2` Kontrolować zmienia rozmiar do wypełnienia komórki.</span><span class="sxs-lookup"><span data-stu-id="8b31c-170">The `elementHost2` control resizes to fill the cell.</span></span>  
  
6.  <span data-ttu-id="8b31c-171">Wybierz <xref:System.Windows.Forms.TableLayoutPanel> formantu.</span><span class="sxs-lookup"><span data-stu-id="8b31c-171">Select the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
7.  <span data-ttu-id="8b31c-172">Ustaw wartość jego <xref:System.Windows.Forms.Control.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Top>.</span><span class="sxs-lookup"><span data-stu-id="8b31c-172">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Top>.</span></span>  
  
8.  <span data-ttu-id="8b31c-173">Wybierz `elementHost3`.</span><span class="sxs-lookup"><span data-stu-id="8b31c-173">Select `elementHost3`.</span></span>  
  
9. <span data-ttu-id="8b31c-174">Ustaw wartość jego <xref:System.Windows.Forms.Control.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="8b31c-174">Set the value of its <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
     <span data-ttu-id="8b31c-175">`elementHost3` Kontrolować zmienia rozmiar w celu wypełnienia pozostałego miejsca na formularzu.</span><span class="sxs-lookup"><span data-stu-id="8b31c-175">The `elementHost3` control resizes to fill the remaining space on the form.</span></span>  
  
10. <span data-ttu-id="8b31c-176">Zmień rozmiar formularza.</span><span class="sxs-lookup"><span data-stu-id="8b31c-176">Resize the form.</span></span>  
  
     <span data-ttu-id="8b31c-177">Wszystkie trzy <xref:System.Windows.Forms.Integration.ElementHost> odpowiednio zmienić rozmiar kontrolki.</span><span class="sxs-lookup"><span data-stu-id="8b31c-177">All three <xref:System.Windows.Forms.Integration.ElementHost> controls resize appropriately.</span></span>  
  
     <span data-ttu-id="8b31c-178">Aby uzyskać więcej informacji, zobacz [porady: zakotwiczenie i formantów podrzędnych Dock w formancie TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span><span class="sxs-lookup"><span data-stu-id="8b31c-178">For more information, see [How to: Anchor and Dock Child Controls in a TableLayoutPanel Control](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b31c-179">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8b31c-179">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="8b31c-180">Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8b31c-180">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="8b31c-181">Instrukcje: wyrównywanie kontrolki z krawędziami formularzy w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="8b31c-181">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 [<span data-ttu-id="8b31c-182">Przewodnik: rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania</span><span class="sxs-lookup"><span data-stu-id="8b31c-182">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="8b31c-183">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="8b31c-183">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="8b31c-184">Korzystanie z kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="8b31c-184">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="8b31c-185">Projektant WPF</span><span class="sxs-lookup"><span data-stu-id="8b31c-185">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
