---
title: "Wskazówki: przypisywanie zawartości WPF na formularzach systemu Windows w czasie projektowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0fa9e40a0a32d0bc9484a86da0f94d62f5c25aa7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-assigning-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="2d78c-102">Wskazówki: przypisywanie zawartości WPF na formularzach systemu Windows w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="2d78c-102">Walkthrough: Assigning WPF Content on Windows Forms at Design Time</span></span>
<span data-ttu-id="2d78c-103">W tym przewodniku opisano sposób wybierz typy formantów systemu Windows Presentation Foundation (WPF), które mają być wyświetlane w formularzu.</span><span class="sxs-lookup"><span data-stu-id="2d78c-103">This walkthrough show you how to select the Windows Presentation Foundation (WPF) control types you want to display on your form.</span></span> <span data-ttu-id="2d78c-104">Możesz wybrać wszystkie typy formantów WPF, które są zawarte w projekcie.</span><span class="sxs-lookup"><span data-stu-id="2d78c-104">You can select any WPF control types which are included in your project.</span></span>  
  
 <span data-ttu-id="2d78c-105">W tym przewodniku należy wykonać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="2d78c-105">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="2d78c-106">Tworzenie projektu.</span><span class="sxs-lookup"><span data-stu-id="2d78c-106">Create the project.</span></span>  
  
-   <span data-ttu-id="2d78c-107">Utwórz typy formantów WPF.</span><span class="sxs-lookup"><span data-stu-id="2d78c-107">Create the WPF control types.</span></span>  
  
-   <span data-ttu-id="2d78c-108">Wybierz formantów WPF.</span><span class="sxs-lookup"><span data-stu-id="2d78c-108">Select WPF controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2d78c-109">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="2d78c-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="2d78c-110">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="2d78c-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="2d78c-111">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="2d78c-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2d78c-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="2d78c-112">Prerequisites</span></span>  
 <span data-ttu-id="2d78c-113">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="2d78c-113">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="2d78c-114">.</span><span class="sxs-lookup"><span data-stu-id="2d78c-114">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="2d78c-115">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="2d78c-115">Creating the Project</span></span>  
 <span data-ttu-id="2d78c-116">Pierwszym krokiem jest utworzenie projektu formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2d78c-116">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2d78c-117">Jeżeli hostowanie zawartości WPF, obsługiwane są tylko C# i Visual Basic, projekty.</span><span class="sxs-lookup"><span data-stu-id="2d78c-117">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="2d78c-118">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="2d78c-118">To create the project</span></span>  
  
-   <span data-ttu-id="2d78c-119">Utwórz nowy projekt aplikacji formularzy systemu Windows w języku Visual Basic lub Visual C# o nazwie `SelectingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="2d78c-119">Create a new Windows Forms Application project in Visual Basic or Visual C# named `SelectingWpfContent`.</span></span>  
  
## <a name="creating-the-wpf-control-types"></a><span data-ttu-id="2d78c-120">Tworzenie typy formantów WPF</span><span class="sxs-lookup"><span data-stu-id="2d78c-120">Creating the WPF Control Types</span></span>  
 <span data-ttu-id="2d78c-121">Po dodaniu typy formantów WPF do projektu może obsługiwać je w różnych <xref:System.Windows.Forms.Integration.ElementHost> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="2d78c-121">After you add WPF control types to the project, you can host them in different <xref:System.Windows.Forms.Integration.ElementHost> controls.</span></span>  
  
#### <a name="to-create-wpf-control-types"></a><span data-ttu-id="2d78c-122">Aby utworzyć typy formantów WPF</span><span class="sxs-lookup"><span data-stu-id="2d78c-122">To create WPF control types</span></span>  
  
1.  <span data-ttu-id="2d78c-123">Dodaj nowy WPF <xref:System.Windows.Controls.UserControl> projektu do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="2d78c-123">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="2d78c-124">Użyj domyślnej nazwy dla typu formantu `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="2d78c-124">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="2d78c-125">Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie nowego WPF zawartości w formularzach systemu Windows w czasie projektowania](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="2d78c-125">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="2d78c-126">W widoku Projekt, upewnij się, że `UserControl1` jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="2d78c-126">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="2d78c-127">Aby uzyskać więcej informacji, zobacz [porady: Wybierz i Przenieś elementy na powierzchnię projektu](http://msdn.microsoft.com/en-us/54cb70b6-b35b-46e4-a0cc-65189399c474).</span><span class="sxs-lookup"><span data-stu-id="2d78c-127">For more information, see [How to: Select and Move Elements on the Design Surface](http://msdn.microsoft.com/en-us/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="2d78c-128">W **właściwości** okna, ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości `200`.</span><span class="sxs-lookup"><span data-stu-id="2d78c-128">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="2d78c-129">Dodaj <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> formant <xref:System.Windows.Controls.UserControl> i ustaw wartość <xref:System.Windows.Controls.TextBox.Text%2A> właściwości **hostowanego zawartości**.</span><span class="sxs-lookup"><span data-stu-id="2d78c-129">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>  
  
5.  <span data-ttu-id="2d78c-130">Dodaj drugi WPF <xref:System.Windows.Controls.UserControl> do projektu.</span><span class="sxs-lookup"><span data-stu-id="2d78c-130">Add a second WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="2d78c-131">Użyj domyślnej nazwy dla typu formantu `UserControl2.xaml`.</span><span class="sxs-lookup"><span data-stu-id="2d78c-131">Use the default name for the control type, `UserControl2.xaml`.</span></span>  
  
6.  <span data-ttu-id="2d78c-132">W **właściwości** okna, ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości `200`.</span><span class="sxs-lookup"><span data-stu-id="2d78c-132">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
7.  <span data-ttu-id="2d78c-133">Dodaj <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> formant <xref:System.Windows.Controls.UserControl> i ustaw wartość <xref:System.Windows.Controls.TextBox.Text%2A> właściwości **hostowanego zawartości 2**.</span><span class="sxs-lookup"><span data-stu-id="2d78c-133">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content 2**.</span></span>  
  
 <span data-ttu-id="2d78c-134">**Uwaga** ogólnie rzecz biorąc, należy udostępnić dokładniejsze zawartości WPF.</span><span class="sxs-lookup"><span data-stu-id="2d78c-134">**Note** In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="2d78c-135"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Kontroli jest tu używany wyłącznie w celach ilustracyjnych.</span><span class="sxs-lookup"><span data-stu-id="2d78c-135">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>  
  
1.  <span data-ttu-id="2d78c-136">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="2d78c-136">Build the project.</span></span>  
  
## <a name="selecting-wpf-controls"></a><span data-ttu-id="2d78c-137">Zaznaczanie formantów WPF</span><span class="sxs-lookup"><span data-stu-id="2d78c-137">Selecting WPF Controls</span></span>  
 <span data-ttu-id="2d78c-138">Można przypisać różne zawartości WPF <xref:System.Windows.Forms.Integration.ElementHost> kontroli, która obecnie prowadzi hosting zawartości.</span><span class="sxs-lookup"><span data-stu-id="2d78c-138">You can assign different WPF content to an <xref:System.Windows.Forms.Integration.ElementHost> control, which is already hosting content.</span></span>  
  
#### <a name="to-select-wpf-controls"></a><span data-ttu-id="2d78c-139">Aby wybrać formantów WPF</span><span class="sxs-lookup"><span data-stu-id="2d78c-139">To select WPF controls</span></span>  
  
1.  <span data-ttu-id="2d78c-140">Otwórz `Form1` w narzędziu Projektant dla formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2d78c-140">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="2d78c-141">W **przybornika**, kliknij dwukrotnie `UserControl1` można utworzyć wystąpienia `UserControl1` w formularzu.</span><span class="sxs-lookup"><span data-stu-id="2d78c-141">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="2d78c-142">Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="2d78c-142">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3.  <span data-ttu-id="2d78c-143">W panelu tagów inteligentnych dla `elementHost1`, otwórz **wybierz hostowanej zawartości** listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="2d78c-143">In the smart tag panel for `elementHost1`, open the **Select Hosted Content** drop-down list.</span></span>  
  
4.  <span data-ttu-id="2d78c-144">Wybierz **UserControl2** w polu listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="2d78c-144">Select **UserControl2** from the drop-down list box.</span></span>  
  
     <span data-ttu-id="2d78c-145">`elementHost1` Kontroli teraz udostępnia wystąpienie `UserControl2` typu.</span><span class="sxs-lookup"><span data-stu-id="2d78c-145">The `elementHost1` control now hosts an instance of the `UserControl2` type.</span></span>  
  
5.  <span data-ttu-id="2d78c-146">W **właściwości** okna, upewnij się, że <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> właściwość jest ustawiona na **UserControl2**.</span><span class="sxs-lookup"><span data-stu-id="2d78c-146">In the **Properties** window, confirm that the <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl2**.</span></span>  
  
6.  <span data-ttu-id="2d78c-147">Z **przybornika**w **współdziałanie WPF** grupy, przeciągnij <xref:System.Windows.Forms.Integration.ElementHost> sterowania do formularza.</span><span class="sxs-lookup"><span data-stu-id="2d78c-147">From the **Toolbox**, in the **WPF Interoperability** group, drag an <xref:System.Windows.Forms.Integration.ElementHost> control onto the form.</span></span>  
  
     <span data-ttu-id="2d78c-148">Domyślna nazwa nowego formantu jest `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="2d78c-148">The default name for the new control is `elementHost2`.</span></span>  
  
7.  <span data-ttu-id="2d78c-149">W panelu tagów inteligentnych dla `elementHost2`, otwórz **wybierz hostowanej zawartości** listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="2d78c-149">In the smart tag panel for `elementHost2`, open the **Select Hosted Content** drop-down list.</span></span>  
  
8.  <span data-ttu-id="2d78c-150">Wybierz **UserControl1** z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="2d78c-150">Select **UserControl1** from the drop-down list.</span></span>  
  
9. <span data-ttu-id="2d78c-151">`elementHost2` Kontroli teraz udostępnia wystąpienie `UserControl1` typu.</span><span class="sxs-lookup"><span data-stu-id="2d78c-151">The `elementHost2` control now hosts an instance of the `UserControl1` type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d78c-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d78c-152">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="2d78c-153">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="2d78c-153">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="2d78c-154">Korzystanie z formantów WPF</span><span class="sxs-lookup"><span data-stu-id="2d78c-154">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="2d78c-155">Projektant WPF</span><span class="sxs-lookup"><span data-stu-id="2d78c-155">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
