---
title: 'Wskazówki: przypisywanie zawartości WPF na formularzach systemu Windows w czasie projektowania'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
ms.openlocfilehash: 6db75e9d8ec5aeb1a0c7310d39391f8f264649d3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43868196"
---
# <a name="walkthrough-assigning-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="d8f93-102">Wskazówki: przypisywanie zawartości WPF na formularzach systemu Windows w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="d8f93-102">Walkthrough: Assigning WPF Content on Windows Forms at Design Time</span></span>
<span data-ttu-id="d8f93-103">W tym instruktażu dowiesz się, jak wybrać typy kontrolek Windows Presentation Foundation (WPF), które mają być wyświetlane w formularzu.</span><span class="sxs-lookup"><span data-stu-id="d8f93-103">This walkthrough show you how to select the Windows Presentation Foundation (WPF) control types you want to display on your form.</span></span> <span data-ttu-id="d8f93-104">Możesz wybrać wszystkie typy kontrolek WPF, które są zawarte w projekcie.</span><span class="sxs-lookup"><span data-stu-id="d8f93-104">You can select any WPF control types which are included in your project.</span></span>  
  
 <span data-ttu-id="d8f93-105">W tym przewodniku należy wykonać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="d8f93-105">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="d8f93-106">Utwórz projekt.</span><span class="sxs-lookup"><span data-stu-id="d8f93-106">Create the project.</span></span>  
  
-   <span data-ttu-id="d8f93-107">Tworzenie typów formantów WPF.</span><span class="sxs-lookup"><span data-stu-id="d8f93-107">Create the WPF control types.</span></span>  
  
-   <span data-ttu-id="d8f93-108">Wybierz kontrolek WPF.</span><span class="sxs-lookup"><span data-stu-id="d8f93-108">Select WPF controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8f93-109">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="d8f93-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d8f93-110">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="d8f93-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d8f93-111">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="d8f93-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d8f93-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="d8f93-112">Prerequisites</span></span>  
 <span data-ttu-id="d8f93-113">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="d8f93-113">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="d8f93-114">.</span><span class="sxs-lookup"><span data-stu-id="d8f93-114">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="d8f93-115">Tworzenie projektu</span><span class="sxs-lookup"><span data-stu-id="d8f93-115">Creating the Project</span></span>  
 <span data-ttu-id="d8f93-116">Pierwszym krokiem jest utworzenie projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d8f93-116">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8f93-117">Gdy hosting zawartości WPF, obsługiwane są tylko C# i projektach języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d8f93-117">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="d8f93-118">Aby utworzyć projekt</span><span class="sxs-lookup"><span data-stu-id="d8f93-118">To create the project</span></span>  
  
-   <span data-ttu-id="d8f93-119">Tworzenie nowego projektu aplikacji formularzy Windows w języku Visual Basic lub Visual C# o nazwie `SelectingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="d8f93-119">Create a new Windows Forms Application project in Visual Basic or Visual C# named `SelectingWpfContent`.</span></span>  
  
## <a name="creating-the-wpf-control-types"></a><span data-ttu-id="d8f93-120">Tworzenie typów formantów WPF</span><span class="sxs-lookup"><span data-stu-id="d8f93-120">Creating the WPF Control Types</span></span>  
 <span data-ttu-id="d8f93-121">Po dodaniu typów formantów WPF do projektu, można umieścić je w różnych <xref:System.Windows.Forms.Integration.ElementHost> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="d8f93-121">After you add WPF control types to the project, you can host them in different <xref:System.Windows.Forms.Integration.ElementHost> controls.</span></span>  
  
#### <a name="to-create-wpf-control-types"></a><span data-ttu-id="d8f93-122">Aby utworzyć typy kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="d8f93-122">To create WPF control types</span></span>  
  
1.  <span data-ttu-id="d8f93-123">Dodaj nowe WPF <xref:System.Windows.Controls.UserControl> projektu do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="d8f93-123">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="d8f93-124">Użyj domyślnej nazwy dla kontrolek typu `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="d8f93-124">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="d8f93-125">Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie nowego WPF zawartości na formularzach Windows Forms w czasie projektowania](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="d8f93-125">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="d8f93-126">W widoku Projekt, upewnij się, że `UserControl1` jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="d8f93-126">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="d8f93-127">Aby uzyskać więcej informacji, zobacz [jak: Select i Przesuń elementy na powierzchni projektowej](https://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span><span class="sxs-lookup"><span data-stu-id="d8f93-127">For more information, see [How to: Select and Move Elements on the Design Surface](https://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).</span></span>  
  
3.  <span data-ttu-id="d8f93-128">W **właściwości** okna, ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości `200`.</span><span class="sxs-lookup"><span data-stu-id="d8f93-128">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4.  <span data-ttu-id="d8f93-129">Dodaj <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> kontrolę <xref:System.Windows.Controls.UserControl> i ustaw wartość <xref:System.Windows.Controls.TextBox.Text%2A> właściwości **hostowanej zawartości**.</span><span class="sxs-lookup"><span data-stu-id="d8f93-129">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>  
  
5.  <span data-ttu-id="d8f93-130">Dodaj drugi WPF <xref:System.Windows.Controls.UserControl> do projektu.</span><span class="sxs-lookup"><span data-stu-id="d8f93-130">Add a second WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="d8f93-131">Użyj domyślnej nazwy dla kontrolek typu `UserControl2.xaml`.</span><span class="sxs-lookup"><span data-stu-id="d8f93-131">Use the default name for the control type, `UserControl2.xaml`.</span></span>  
  
6.  <span data-ttu-id="d8f93-132">W **właściwości** okna, ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości `200`.</span><span class="sxs-lookup"><span data-stu-id="d8f93-132">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
7.  <span data-ttu-id="d8f93-133">Dodaj <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> kontrolę <xref:System.Windows.Controls.UserControl> i ustaw wartość <xref:System.Windows.Controls.TextBox.Text%2A> właściwości **hostowanej zawartości 2**.</span><span class="sxs-lookup"><span data-stu-id="d8f93-133">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content 2**.</span></span>  
  
 <span data-ttu-id="d8f93-134">**Uwaga** ogólnie rzecz biorąc, należy obsługiwać bardziej złożone zawartości WPF.</span><span class="sxs-lookup"><span data-stu-id="d8f93-134">**Note** In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="d8f93-135"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Kontroli jest tu używany wyłącznie w celach opisowy.</span><span class="sxs-lookup"><span data-stu-id="d8f93-135">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>  
  
1.  <span data-ttu-id="d8f93-136">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="d8f93-136">Build the project.</span></span>  
  
## <a name="selecting-wpf-controls"></a><span data-ttu-id="d8f93-137">Zaznaczanie kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="d8f93-137">Selecting WPF Controls</span></span>  
 <span data-ttu-id="d8f93-138">Można przypisać różne zawartości WPF na <xref:System.Windows.Forms.Integration.ElementHost> formant, który jest już hosting zawartości.</span><span class="sxs-lookup"><span data-stu-id="d8f93-138">You can assign different WPF content to an <xref:System.Windows.Forms.Integration.ElementHost> control, which is already hosting content.</span></span>  
  
#### <a name="to-select-wpf-controls"></a><span data-ttu-id="d8f93-139">Aby wybrać kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="d8f93-139">To select WPF controls</span></span>  
  
1.  <span data-ttu-id="d8f93-140">Otwórz `Form1` w programie Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="d8f93-140">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="d8f93-141">W **przybornika**, kliknij dwukrotnie `UserControl1` do utworzenia wystąpienia `UserControl1` w formularzu.</span><span class="sxs-lookup"><span data-stu-id="d8f93-141">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="d8f93-142">Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="d8f93-142">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3.  <span data-ttu-id="d8f93-143">W panelu tagi inteligentne dla `elementHost1`, otwórz **zaznacz hostowana zawartość** listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="d8f93-143">In the smart tag panel for `elementHost1`, open the **Select Hosted Content** drop-down list.</span></span>  
  
4.  <span data-ttu-id="d8f93-144">Wybierz **UserControl2** w polu listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="d8f93-144">Select **UserControl2** from the drop-down list box.</span></span>  
  
     <span data-ttu-id="d8f93-145">`elementHost1` Kontroli teraz udostępnia wystąpienie `UserControl2` typu.</span><span class="sxs-lookup"><span data-stu-id="d8f93-145">The `elementHost1` control now hosts an instance of the `UserControl2` type.</span></span>  
  
5.  <span data-ttu-id="d8f93-146">W **właściwości** okna, upewnij się, że <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> właściwość jest ustawiona na **UserControl2**.</span><span class="sxs-lookup"><span data-stu-id="d8f93-146">In the **Properties** window, confirm that the <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl2**.</span></span>  
  
6.  <span data-ttu-id="d8f93-147">Z **przybornika**w **współdziałanie WPF** grupy, przeciągnij <xref:System.Windows.Forms.Integration.ElementHost> formant na formularzu.</span><span class="sxs-lookup"><span data-stu-id="d8f93-147">From the **Toolbox**, in the **WPF Interoperability** group, drag an <xref:System.Windows.Forms.Integration.ElementHost> control onto the form.</span></span>  
  
     <span data-ttu-id="d8f93-148">Domyślna nazwa dla nowego formantu to `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="d8f93-148">The default name for the new control is `elementHost2`.</span></span>  
  
7.  <span data-ttu-id="d8f93-149">W panelu tagi inteligentne dla `elementHost2`, otwórz **zaznacz hostowana zawartość** listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="d8f93-149">In the smart tag panel for `elementHost2`, open the **Select Hosted Content** drop-down list.</span></span>  
  
8.  <span data-ttu-id="d8f93-150">Wybierz **UserControl1** z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="d8f93-150">Select **UserControl1** from the drop-down list.</span></span>  
  
9. <span data-ttu-id="d8f93-151">`elementHost2` Kontroli teraz udostępnia wystąpienie `UserControl1` typu.</span><span class="sxs-lookup"><span data-stu-id="d8f93-151">The `elementHost2` control now hosts an instance of the `UserControl1` type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8f93-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8f93-152">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="d8f93-153">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="d8f93-153">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="d8f93-154">Korzystanie z kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="d8f93-154">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="d8f93-155">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d8f93-155">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
