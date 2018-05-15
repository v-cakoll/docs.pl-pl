---
title: 'Wskazówki: zmienianie właściwości hostowanego elementu WPF w czasie projektowania'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], changing properties at design time
- Windows Forms, changing properties of WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- interoperability [WPF]
ms.assetid: a1f7a90c-0bbb-4781-8c3c-8cc8bef2488d
ms.openlocfilehash: d17273f52d0cef118b79fef03af72522f6677073
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time"></a><span data-ttu-id="4a7ad-102">Wskazówki: zmienianie właściwości hostowanego elementu WPF w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="4a7ad-102">Walkthrough: Changing Properties of a Hosted WPF Element at Design Time</span></span>
<span data-ttu-id="4a7ad-103">W tym przewodniku przedstawiono sposób zmiany wartości właściwości kontrolki Windows Presentation Foundation (WPF) obsługiwanych na formularzu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="4a7ad-103">This walkthrough shows you how to change property values of a Windows Presentation Foundation (WPF) control hosted on a Windows Form.</span></span>  
  
 <span data-ttu-id="4a7ad-104">W tym przewodniku należy wykonać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="4a7ad-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="4a7ad-105">Tworzenie projektu.</span><span class="sxs-lookup"><span data-stu-id="4a7ad-105">Create the project.</span></span>  
  
-   <span data-ttu-id="4a7ad-106">Tworzenie formantu WPF.</span><span class="sxs-lookup"><span data-stu-id="4a7ad-106">Create the WPF control.</span></span>  
  
-   <span data-ttu-id="4a7ad-107">Host formantów WPF w formularzach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="4a7ad-107">Host the WPF controls on a Windows Form.</span></span>  
  
-   <span data-ttu-id="4a7ad-108">Aby zmienić wartości właściwości za pomocą projektanta WPF dla programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4a7ad-108">Use the WPF Designer for Visual Studio to change property values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a7ad-109">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="4a7ad-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="4a7ad-110">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="4a7ad-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="4a7ad-111">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="4a7ad-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4a7ad-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="4a7ad-112">Prerequisites</span></span>  
 <span data-ttu-id="4a7ad-113">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="4a7ad-113">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="4a7ad-114">.</span><span class="sxs-lookup"><span data-stu-id="4a7ad-114">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="4a7ad-115">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="4a7ad-115">Creating the Project</span></span>  
 <span data-ttu-id="4a7ad-116">Pierwszym krokiem jest utworzenie projektu formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="4a7ad-116">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a7ad-117">Jeżeli hostowanie zawartości WPF, obsługiwane są tylko C# i Visual Basic, projekty.</span><span class="sxs-lookup"><span data-stu-id="4a7ad-117">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="4a7ad-118">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="4a7ad-118">To create the project</span></span>  
  
-   <span data-ttu-id="4a7ad-119">Utwórz nowy projekt aplikacji formularzy systemu Windows w języku Visual Basic lub Visual C# o nazwie `WpfHost`.</span><span class="sxs-lookup"><span data-stu-id="4a7ad-119">Create a new Windows Forms Application project in Visual Basic or Visual C# named `WpfHost`.</span></span>  
  
## <a name="creating-the-wpf-control"></a><span data-ttu-id="4a7ad-120">Tworzenie formantu WPF</span><span class="sxs-lookup"><span data-stu-id="4a7ad-120">Creating the WPF Control</span></span>  
 <span data-ttu-id="4a7ad-121">Po dodaniu formantu WPF do projektu można rozmieścić go w formularzu.</span><span class="sxs-lookup"><span data-stu-id="4a7ad-121">After you add a WPF control to the project, you can arrange it on the form.</span></span>  
  
#### <a name="to-create-wpf-controls"></a><span data-ttu-id="4a7ad-122">Aby utworzyć formantów WPF</span><span class="sxs-lookup"><span data-stu-id="4a7ad-122">To create WPF controls</span></span>  
  
1.  <span data-ttu-id="4a7ad-123">Dodaj nowy WPF <xref:System.Windows.Controls.UserControl> do projektu.</span><span class="sxs-lookup"><span data-stu-id="4a7ad-123">Add a new WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="4a7ad-124">Użyj domyślnej nazwy dla typu formantu `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="4a7ad-124">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="4a7ad-125">Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie nowego WPF zawartości w formularzach systemu Windows w czasie projektowania](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="4a7ad-125">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="4a7ad-126">W **właściwości** okna, ustaw wartość <xref:System.Windows.Controls.Control.Background%2A> właściwości `Blue`.</span><span class="sxs-lookup"><span data-stu-id="4a7ad-126">In the **Properties** window, set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>  
  
3.  <span data-ttu-id="4a7ad-127">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="4a7ad-127">Build the project.</span></span>  
  
## <a name="changing-property-values-on-the-wpf-control"></a><span data-ttu-id="4a7ad-128">Zmiana wartości właściwości w kontrolce WPF</span><span class="sxs-lookup"><span data-stu-id="4a7ad-128">Changing Property Values on the WPF Control</span></span>  
 <span data-ttu-id="4a7ad-129"><xref:System.Windows.Forms.Integration.ElementHost> Tagów inteligentnych można łatwo zmienić właściwości WPF hostowanej zawartości przy użyciu narzędzia Projektant WPF.</span><span class="sxs-lookup"><span data-stu-id="4a7ad-129">The <xref:System.Windows.Forms.Integration.ElementHost> smart tag makes it easy to change properties of hosted WPF content by using the WPF Designer.</span></span>  
  
#### <a name="to-host-a-wpf-control"></a><span data-ttu-id="4a7ad-130">Do hostowania formantu WPF</span><span class="sxs-lookup"><span data-stu-id="4a7ad-130">To host a WPF control</span></span>  
  
1.  <span data-ttu-id="4a7ad-131">Otwórz `Form1` w narzędziu Projektant dla formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="4a7ad-131">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="4a7ad-132">W **przybornika**w **formanty użytkownika WPF** karcie, kliknij dwukrotnie `UserControl1` można utworzyć wystąpienia `UserControl1` w formularzu.</span><span class="sxs-lookup"><span data-stu-id="4a7ad-132">In the **Toolbox**, in the **WPF User Controls** tab, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="4a7ad-133">Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="4a7ad-133">The instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3.  <span data-ttu-id="4a7ad-134">W **zadania ElementHost** panelu tagów inteligentnych, wybierz opcję **Edytuj hostowana zawartość**.</span><span class="sxs-lookup"><span data-stu-id="4a7ad-134">In the **ElementHost Tasks** smart tag panel, select **Edit Hosted Content**.</span></span>  
  
     <span data-ttu-id="4a7ad-135">UserControl1.xaml zostanie otwarty w Projektancie WPF.</span><span class="sxs-lookup"><span data-stu-id="4a7ad-135">UserControl1.xaml opens in the WPF Designer.</span></span>  
  
4.  <span data-ttu-id="4a7ad-136">W **właściwości** okna, ustaw wartość <xref:System.Windows.Controls.Control.Background%2A> właściwości `Red`.</span><span class="sxs-lookup"><span data-stu-id="4a7ad-136">In the **Properties** window, set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Red`.</span></span>  
  
5.  <span data-ttu-id="4a7ad-137">Skompiluj ponownie projekt.</span><span class="sxs-lookup"><span data-stu-id="4a7ad-137">Rebuild the project.</span></span>  
  
6.  <span data-ttu-id="4a7ad-138">Otwórz `Form1` w narzędziu Projektant dla formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="4a7ad-138">Open `Form1` in the Windows Forms Designer.</span></span>  
  
     <span data-ttu-id="4a7ad-139">Wystąpienie `UserControl1` ma red tło.</span><span class="sxs-lookup"><span data-stu-id="4a7ad-139">The instance of `UserControl1` has a red background.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a7ad-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4a7ad-140">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="4a7ad-141">Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="4a7ad-141">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="4a7ad-142">Instrukcje: wyrównywanie kontrolki z krawędziami formularzy w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="4a7ad-142">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 [<span data-ttu-id="4a7ad-143">Przewodnik: rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania</span><span class="sxs-lookup"><span data-stu-id="4a7ad-143">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="4a7ad-144">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="4a7ad-144">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="4a7ad-145">Korzystanie z kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="4a7ad-145">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="4a7ad-146">Projektant WPF</span><span class="sxs-lookup"><span data-stu-id="4a7ad-146">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
