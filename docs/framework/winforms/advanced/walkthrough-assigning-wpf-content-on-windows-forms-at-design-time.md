---
title: 'Przewodnik: Przypisywanie zawartości WPF na formularzach systemu Windows w czasie projektowania'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bc5f5e2d8808c0a60df721bf2c0ed76b45ef49a0
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666260"
---
# <a name="walkthrough-assign-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="a5197-102">Przewodnik: Przypisywanie zawartości WPF na Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="a5197-102">Walkthrough: Assign WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="a5197-103">W tym artykule pokazano, jak wybrać typy formantów Windows Presentation Foundation (WPF), które mają być wyświetlane w formularzu.</span><span class="sxs-lookup"><span data-stu-id="a5197-103">This article show you how to select the Windows Presentation Foundation (WPF) control types you want to display on your form.</span></span> <span data-ttu-id="a5197-104">Można wybrać dowolne typy formantów WPF, które są uwzględnione w projekcie.</span><span class="sxs-lookup"><span data-stu-id="a5197-104">You can select any WPF control types which are included in your project.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a5197-105">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="a5197-105">Prerequisites</span></span>

<span data-ttu-id="a5197-106">Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a5197-106">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="a5197-107">Utwórz projekt</span><span class="sxs-lookup"><span data-stu-id="a5197-107">Create the project</span></span>

<span data-ttu-id="a5197-108">Otwórz program Visual Studio i Utwórz nowy projekt aplikacji Windows Forms w Visual Basic lub C# wizualizacji `SelectingWpfContent`o nazwie.</span><span class="sxs-lookup"><span data-stu-id="a5197-108">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `SelectingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="a5197-109">W przypadku hostowania zawartości WPF C# obsługiwane są tylko projekty i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a5197-109">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="a5197-110">Tworzenie typów formantów WPF</span><span class="sxs-lookup"><span data-stu-id="a5197-110">Create the WPF control types</span></span>

<span data-ttu-id="a5197-111">Po dodaniu typów formantów WPF do projektu można hostować je w różnych <xref:System.Windows.Forms.Integration.ElementHost> kontrolkach.</span><span class="sxs-lookup"><span data-stu-id="a5197-111">After you add WPF control types to the project, you can host them in different <xref:System.Windows.Forms.Integration.ElementHost> controls.</span></span>

1. <span data-ttu-id="a5197-112">Dodaj nowy projekt WPF <xref:System.Windows.Controls.UserControl> do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="a5197-112">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="a5197-113">Użyj domyślnej nazwy dla typu formantu, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="a5197-113">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="a5197-114">Aby uzyskać więcej informacji, [zobacz Przewodnik: Tworzenie nowej zawartości WPF na Windows Forms w czasie](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)projektowania.</span><span class="sxs-lookup"><span data-stu-id="a5197-114">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="a5197-115">W widok Projekt upewnij się, że `UserControl1` jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="a5197-115">In Design view, make sure that `UserControl1` is selected.</span></span>

3. <span data-ttu-id="a5197-116">W oknie **Właściwości** ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> właściwości i <xref:System.Windows.FrameworkElement.Height%2A> na **200**.</span><span class="sxs-lookup"><span data-stu-id="a5197-116">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

4. <span data-ttu-id="a5197-117">Dodaj kontrolkę <xref:System.Windows.Controls.UserControl> do i <xref:System.Windows.Controls.TextBox.Text%2A> ustaw wartość właściwości na **hostowaną zawartość**. <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a5197-117">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

5. <span data-ttu-id="a5197-118">Dodaj drugi WPF <xref:System.Windows.Controls.UserControl> do projektu.</span><span class="sxs-lookup"><span data-stu-id="a5197-118">Add a second WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="a5197-119">Użyj domyślnej nazwy dla typu formantu, `UserControl2.xaml`.</span><span class="sxs-lookup"><span data-stu-id="a5197-119">Use the default name for the control type, `UserControl2.xaml`.</span></span>

6. <span data-ttu-id="a5197-120">W oknie **Właściwości** ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> właściwości i <xref:System.Windows.FrameworkElement.Height%2A> na **200**.</span><span class="sxs-lookup"><span data-stu-id="a5197-120">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to **200**.</span></span>

7. <span data-ttu-id="a5197-121">Dodaj kontrolkę <xref:System.Windows.Controls.UserControl> do i <xref:System.Windows.Controls.TextBox.Text%2A> ustaw wartość właściwości na **hostowaną zawartość 2**. <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a5197-121">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content 2**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="a5197-122">Ogólnie rzecz biorąc, należy hostować bardziej zaawansowaną zawartość WPF.</span><span class="sxs-lookup"><span data-stu-id="a5197-122">In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="a5197-123"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Kontrolka jest używana w tym miejscu tylko do celów informacyjnych.</span><span class="sxs-lookup"><span data-stu-id="a5197-123">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

8. <span data-ttu-id="a5197-124">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="a5197-124">Build the project.</span></span>

## <a name="select-wpf-controls"></a><span data-ttu-id="a5197-125">Wybieranie formantów WPF</span><span class="sxs-lookup"><span data-stu-id="a5197-125">Select WPF controls</span></span>

<span data-ttu-id="a5197-126">Można przypisać inną zawartość WPF do <xref:System.Windows.Forms.Integration.ElementHost> kontrolki, która jest już hostem zawartości.</span><span class="sxs-lookup"><span data-stu-id="a5197-126">You can assign different WPF content to an <xref:System.Windows.Forms.Integration.ElementHost> control, which is already hosting content.</span></span>

1. <span data-ttu-id="a5197-127">Otwórz `Form1` w Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a5197-127">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="a5197-128">W **przyborniku**kliknij `UserControl1` dwukrotnie, aby utworzyć wystąpienie elementu `UserControl1` w formularzu.</span><span class="sxs-lookup"><span data-stu-id="a5197-128">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

   <span data-ttu-id="a5197-129">Wystąpienie `UserControl1` jest hostowane w nowym <xref:System.Windows.Forms.Integration.ElementHost> formancie o nazwie `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="a5197-129">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

3. <span data-ttu-id="a5197-130">W panelu tagów inteligentnych dla programu `elementHost1`Otwórz listę rozwijaną **Wybierz hostowaną zawartość** .</span><span class="sxs-lookup"><span data-stu-id="a5197-130">In the smart tag panel for `elementHost1`, open the **Select Hosted Content** drop-down list.</span></span>

4. <span data-ttu-id="a5197-131">W polu listy rozwijanej wybierz pozycję **UserControl2** .</span><span class="sxs-lookup"><span data-stu-id="a5197-131">Select **UserControl2** from the drop-down list box.</span></span>

   <span data-ttu-id="a5197-132">Kontrolka teraz obsługuje wystąpienie `UserControl2` typu. `elementHost1`</span><span class="sxs-lookup"><span data-stu-id="a5197-132">The `elementHost1` control now hosts an instance of the `UserControl2` type.</span></span>

5. <span data-ttu-id="a5197-133">W oknie **Właściwości** upewnij się, że <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> właściwość jest ustawiona na **UserControl2**.</span><span class="sxs-lookup"><span data-stu-id="a5197-133">In the **Properties** window, confirm that the <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl2**.</span></span>

6. <span data-ttu-id="a5197-134">Z **przybornika**w grupie współdziałanie **WPF** przeciągnij <xref:System.Windows.Forms.Integration.ElementHost> kontrolkę na formularz.</span><span class="sxs-lookup"><span data-stu-id="a5197-134">From the **Toolbox**, in the **WPF Interoperability** group, drag an <xref:System.Windows.Forms.Integration.ElementHost> control onto the form.</span></span>

   <span data-ttu-id="a5197-135">Domyślna nazwa nowej kontrolki to `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="a5197-135">The default name for the new control is `elementHost2`.</span></span>

7. <span data-ttu-id="a5197-136">W panelu tagów inteligentnych dla programu `elementHost2`Otwórz listę rozwijaną **Wybierz hostowaną zawartość** .</span><span class="sxs-lookup"><span data-stu-id="a5197-136">In the smart tag panel for `elementHost2`, open the **Select Hosted Content** drop-down list.</span></span>

8. <span data-ttu-id="a5197-137">Wybierz pozycję **UserControl1** z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="a5197-137">Select **UserControl1** from the drop-down list.</span></span>

9. <span data-ttu-id="a5197-138">Kontrolka teraz obsługuje wystąpienie `UserControl1` typu. `elementHost2`</span><span class="sxs-lookup"><span data-stu-id="a5197-138">The `elementHost2` control now hosts an instance of the `UserControl1` type.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5197-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5197-139">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="a5197-140">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="a5197-140">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="a5197-141">Korzystanie z kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="a5197-141">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="a5197-142">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a5197-142">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
