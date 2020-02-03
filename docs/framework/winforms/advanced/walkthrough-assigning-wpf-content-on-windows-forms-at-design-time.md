---
title: Wybierz kontrolki WPF dla Windows Forms
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 19f1dfec282b025f5a1fa367ec5fa9a52472c691
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746813"
---
# <a name="walkthrough-assign-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="c127d-102">Przewodnik: przypisywanie zawartości WPF na Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="c127d-102">Walkthrough: Assign WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="c127d-103">W tym artykule pokazano, jak wybrać typy formantów Windows Presentation Foundation (WPF), które mają być wyświetlane w formularzu.</span><span class="sxs-lookup"><span data-stu-id="c127d-103">This article show you how to select the Windows Presentation Foundation (WPF) control types you want to display on your form.</span></span> <span data-ttu-id="c127d-104">Można wybrać dowolne typy formantów WPF, które są zawarte w projekcie.</span><span class="sxs-lookup"><span data-stu-id="c127d-104">You can select any WPF control types that are included in your project.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c127d-105">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="c127d-105">Prerequisites</span></span>

<span data-ttu-id="c127d-106">Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c127d-106">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="c127d-107">Utwórz projekt</span><span class="sxs-lookup"><span data-stu-id="c127d-107">Create the project</span></span>

<span data-ttu-id="c127d-108">Otwórz program Visual Studio i Utwórz nowy projekt aplikacji Windows Forms w Visual Basic lub wizualizacji C# o nazwie `SelectingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="c127d-108">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `SelectingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="c127d-109">W przypadku hostowania zawartości WPF C# obsługiwane są tylko projekty i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c127d-109">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="c127d-110">Tworzenie typów formantów WPF</span><span class="sxs-lookup"><span data-stu-id="c127d-110">Create the WPF control types</span></span>

<span data-ttu-id="c127d-111">Po dodaniu typów formantów WPF do projektu można hostować je w różnych <xref:System.Windows.Forms.Integration.ElementHost>ych kontrolkach.</span><span class="sxs-lookup"><span data-stu-id="c127d-111">After you add WPF control types to the project, you can host them in different <xref:System.Windows.Forms.Integration.ElementHost> controls.</span></span>

1. <span data-ttu-id="c127d-112">Dodaj nowy projekt WPF <xref:System.Windows.Controls.UserControl> do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="c127d-112">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="c127d-113">Użyj domyślnej nazwy dla typu formantu, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="c127d-113">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="c127d-114">Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie nowej zawartości WPF na Windows Forms w czasie projektowania](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="c127d-114">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="c127d-115">W widok Projekt upewnij się, że wybrano pozycję `UserControl1`.</span><span class="sxs-lookup"><span data-stu-id="c127d-115">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="c127d-116">W oknie **Właściwości** ustaw wartość właściwości <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> na **200**.</span><span class="sxs-lookup"><span data-stu-id="c127d-116">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="c127d-117">Dodaj kontrolkę <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> do <xref:System.Windows.Controls.UserControl> i ustaw wartość właściwości <xref:System.Windows.Controls.TextBox.Text%2A> na **hostowaną zawartość**.</span><span class="sxs-lookup"><span data-stu-id="c127d-117">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

5. <span data-ttu-id="c127d-118">Dodaj drugi <xref:System.Windows.Controls.UserControl> WPF do projektu.</span><span class="sxs-lookup"><span data-stu-id="c127d-118">Add a second WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="c127d-119">Użyj domyślnej nazwy dla typu formantu, `UserControl2.xaml`.</span><span class="sxs-lookup"><span data-stu-id="c127d-119">Use the default name for the control type, `UserControl2.xaml`.</span></span>

6. <span data-ttu-id="c127d-120">W oknie **Właściwości** ustaw wartość właściwości <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> na **200**.</span><span class="sxs-lookup"><span data-stu-id="c127d-120">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

7. <span data-ttu-id="c127d-121">Dodaj kontrolkę <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> do <xref:System.Windows.Controls.UserControl> i ustaw wartość właściwości <xref:System.Windows.Controls.TextBox.Text%2A> na **hostowaną zawartość 2**.</span><span class="sxs-lookup"><span data-stu-id="c127d-121">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content 2**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="c127d-122">Ogólnie rzecz biorąc, należy hostować bardziej zaawansowaną zawartość WPF.</span><span class="sxs-lookup"><span data-stu-id="c127d-122">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="c127d-123">Kontrolka <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> jest używana tutaj tylko do celów informacyjnych.</span><span class="sxs-lookup"><span data-stu-id="c127d-123">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

8. <span data-ttu-id="c127d-124">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="c127d-124">Build the project.</span></span>

## <a name="select-wpf-controls"></a><span data-ttu-id="c127d-125">Wybieranie formantów WPF</span><span class="sxs-lookup"><span data-stu-id="c127d-125">Select WPF controls</span></span>

<span data-ttu-id="c127d-126">Możesz przypisać inną zawartość WPF do kontrolki <xref:System.Windows.Forms.Integration.ElementHost>, która już obsługuje zawartość.</span><span class="sxs-lookup"><span data-stu-id="c127d-126">You can assign different WPF content to an <xref:System.Windows.Forms.Integration.ElementHost> control, which is already hosting content.</span></span>

1. <span data-ttu-id="c127d-127">Otwórz `Form1` w Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="c127d-127">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="c127d-128">W **przyborniku**kliknij dwukrotnie `UserControl1`, aby utworzyć wystąpienie `UserControl1` w formularzu.</span><span class="sxs-lookup"><span data-stu-id="c127d-128">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

   <span data-ttu-id="c127d-129">Wystąpienie `UserControl1` jest hostowane w nowej kontrolce <xref:System.Windows.Forms.Integration.ElementHost> o nazwie `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="c127d-129">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

3. <span data-ttu-id="c127d-130">Na panelu tagów inteligentnych dla `elementHost1`Otwórz listę rozwijaną **Wybierz hostowaną zawartość** .</span><span class="sxs-lookup"><span data-stu-id="c127d-130">In the smart tag panel for `elementHost1`, open the **Select Hosted Content** drop-down list.</span></span>

4. <span data-ttu-id="c127d-131">W polu listy rozwijanej wybierz pozycję **UserControl2** .</span><span class="sxs-lookup"><span data-stu-id="c127d-131">Select **UserControl2** from the drop-down list box.</span></span>

   <span data-ttu-id="c127d-132">Kontrolka `elementHost1` teraz obsługuje wystąpienie typu `UserControl2`.</span><span class="sxs-lookup"><span data-stu-id="c127d-132">The `elementHost1` control now hosts an instance of the `UserControl2` type.</span></span>

5. <span data-ttu-id="c127d-133">W oknie **Właściwości** upewnij się, że właściwość <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> jest ustawiona na **UserControl2**.</span><span class="sxs-lookup"><span data-stu-id="c127d-133">In the **Properties** window, confirm that the <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl2**.</span></span>

6. <span data-ttu-id="c127d-134">Z **przybornika**w grupie **współdziałanie WPF** przeciągnij kontrolkę <xref:System.Windows.Forms.Integration.ElementHost> na formularz.</span><span class="sxs-lookup"><span data-stu-id="c127d-134">From the **Toolbox**, in the **WPF Interoperability** group, drag an <xref:System.Windows.Forms.Integration.ElementHost> control onto the form.</span></span>

   <span data-ttu-id="c127d-135">Domyślna nazwa nowej kontrolki jest `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="c127d-135">The default name for the new control is `elementHost2`.</span></span>

7. <span data-ttu-id="c127d-136">Na panelu tagów inteligentnych dla `elementHost2`Otwórz listę rozwijaną **Wybierz hostowaną zawartość** .</span><span class="sxs-lookup"><span data-stu-id="c127d-136">In the smart tag panel for `elementHost2`, open the **Select Hosted Content** drop-down list.</span></span>

8. <span data-ttu-id="c127d-137">Wybierz pozycję **UserControl1** z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="c127d-137">Select **UserControl1** from the drop-down list.</span></span>

9. <span data-ttu-id="c127d-138">Kontrolka `elementHost2` teraz obsługuje wystąpienie typu `UserControl1`.</span><span class="sxs-lookup"><span data-stu-id="c127d-138">The `elementHost2` control now hosts an instance of the `UserControl1` type.</span></span>

## <a name="see-also"></a><span data-ttu-id="c127d-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c127d-139">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="c127d-140">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="c127d-140">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="c127d-141">Korzystanie z kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="c127d-141">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="c127d-142">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c127d-142">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
