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
ms.openlocfilehash: 09427bfc836f40ca9c7aa76f4904bfe7083bf8dc
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211233"
---
# <a name="walkthrough-assign-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="38c79-102">Przewodnik: Przypisywanie zawartości WPF na formularzach Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="38c79-102">Walkthrough: Assign WPF content on Windows Forms at design time</span></span>

<span data-ttu-id="38c79-103">W tym instruktażu dowiesz się, jak wybrać typy kontrolek Windows Presentation Foundation (WPF), które mają być wyświetlane w formularzu.</span><span class="sxs-lookup"><span data-stu-id="38c79-103">This walkthrough show you how to select the Windows Presentation Foundation (WPF) control types you want to display on your form.</span></span> <span data-ttu-id="38c79-104">Możesz wybrać wszystkie typy kontrolek WPF, które są zawarte w projekcie.</span><span class="sxs-lookup"><span data-stu-id="38c79-104">You can select any WPF control types which are included in your project.</span></span>

<span data-ttu-id="38c79-105">W tym przewodniku należy wykonać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="38c79-105">In this walkthrough, you perform the following tasks:</span></span>

- <span data-ttu-id="38c79-106">Utwórz projekt.</span><span class="sxs-lookup"><span data-stu-id="38c79-106">Create the project.</span></span>

- <span data-ttu-id="38c79-107">Tworzenie typów formantów WPF.</span><span class="sxs-lookup"><span data-stu-id="38c79-107">Create the WPF control types.</span></span>

- <span data-ttu-id="38c79-108">Wybierz kontrolek WPF.</span><span class="sxs-lookup"><span data-stu-id="38c79-108">Select WPF controls.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="38c79-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="38c79-109">Prerequisites</span></span>

<span data-ttu-id="38c79-110">Potrzebujesz programu Visual Studio w celu przeprowadzenia tego instruktażu.</span><span class="sxs-lookup"><span data-stu-id="38c79-110">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="38c79-111">Utwórz projekt</span><span class="sxs-lookup"><span data-stu-id="38c79-111">Create the project</span></span>

<span data-ttu-id="38c79-112">Otwórz program Visual Studio i Utwórz nowy projekt Windows Forms aplikacji w Visual Basic lub Visual C# o nazwie `SelectingWpfContent`.</span><span class="sxs-lookup"><span data-stu-id="38c79-112">Open Visual Studio and create a new Windows Forms Application project in Visual Basic or Visual C# named `SelectingWpfContent`.</span></span>

> [!NOTE]
> <span data-ttu-id="38c79-113">Gdy hosting zawartości WPF, obsługiwane są tylko C# i projektach języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="38c79-113">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>

## <a name="create-the-wpf-control-types"></a><span data-ttu-id="38c79-114">Tworzenie typów formantów WPF</span><span class="sxs-lookup"><span data-stu-id="38c79-114">Create the WPF control types</span></span>

<span data-ttu-id="38c79-115">Po dodaniu typów formantów WPF do projektu, można umieścić je w różnych <xref:System.Windows.Forms.Integration.ElementHost> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="38c79-115">After you add WPF control types to the project, you can host them in different <xref:System.Windows.Forms.Integration.ElementHost> controls.</span></span>

## <a name="create-wpf-control-types"></a><span data-ttu-id="38c79-116">Tworzenie typów formantów WPF</span><span class="sxs-lookup"><span data-stu-id="38c79-116">Create WPF control types</span></span>

1. <span data-ttu-id="38c79-117">Dodaj nowe WPF <xref:System.Windows.Controls.UserControl> projektu do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="38c79-117">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="38c79-118">Użyj domyślnej nazwy dla kontrolek typu `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="38c79-118">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="38c79-119">Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie nowej zawartości WPF na formularzach Windows Forms w czasie projektowania](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="38c79-119">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="38c79-120">W widoku Projekt, upewnij się, że `UserControl1` jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="38c79-120">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="38c79-121">Aby uzyskać więcej informacji, zobacz [jak: Wybierz i Przesuń elementy na powierzchni projektowej](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="38c79-121">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>

3. <span data-ttu-id="38c79-122">W **właściwości** okna, ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości `200`.</span><span class="sxs-lookup"><span data-stu-id="38c79-122">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>

4. <span data-ttu-id="38c79-123">Dodaj <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> kontrolę <xref:System.Windows.Controls.UserControl> i ustaw wartość <xref:System.Windows.Controls.TextBox.Text%2A> właściwości **hostowanej zawartości**.</span><span class="sxs-lookup"><span data-stu-id="38c79-123">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>

5. <span data-ttu-id="38c79-124">Dodaj drugi WPF <xref:System.Windows.Controls.UserControl> do projektu.</span><span class="sxs-lookup"><span data-stu-id="38c79-124">Add a second WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="38c79-125">Użyj domyślnej nazwy dla kontrolek typu `UserControl2.xaml`.</span><span class="sxs-lookup"><span data-stu-id="38c79-125">Use the default name for the control type, `UserControl2.xaml`.</span></span>

6. <span data-ttu-id="38c79-126">W **właściwości** okna, ustaw wartość <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości `200`.</span><span class="sxs-lookup"><span data-stu-id="38c79-126">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>

7. <span data-ttu-id="38c79-127">Dodaj <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> kontrolę <xref:System.Windows.Controls.UserControl> i ustaw wartość <xref:System.Windows.Controls.TextBox.Text%2A> właściwości **hostowanej zawartości 2**.</span><span class="sxs-lookup"><span data-stu-id="38c79-127">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content 2**.</span></span>

 <span data-ttu-id="38c79-128">**Uwaga** ogólnie rzecz biorąc, należy obsługiwać bardziej złożone zawartości WPF.</span><span class="sxs-lookup"><span data-stu-id="38c79-128">**Note** In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="38c79-129"><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> Kontroli jest tu używany wyłącznie w celach opisowy.</span><span class="sxs-lookup"><span data-stu-id="38c79-129">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>

1. <span data-ttu-id="38c79-130">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="38c79-130">Build the project.</span></span>

## <a name="select-wpf-controls"></a><span data-ttu-id="38c79-131">Wybierz kontrolki WPF</span><span class="sxs-lookup"><span data-stu-id="38c79-131">Select WPF controls</span></span>

<span data-ttu-id="38c79-132">Można przypisać różne zawartości WPF na <xref:System.Windows.Forms.Integration.ElementHost> formant, który jest już hosting zawartości.</span><span class="sxs-lookup"><span data-stu-id="38c79-132">You can assign different WPF content to an <xref:System.Windows.Forms.Integration.ElementHost> control, which is already hosting content.</span></span>

1. <span data-ttu-id="38c79-133">Otwórz `Form1` w programie Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="38c79-133">Open `Form1` in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="38c79-134">W **przybornika**, kliknij dwukrotnie `UserControl1` do utworzenia wystąpienia `UserControl1` w formularzu.</span><span class="sxs-lookup"><span data-stu-id="38c79-134">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>

     <span data-ttu-id="38c79-135">Wystąpienie `UserControl1` znajduje się w nowym <xref:System.Windows.Forms.Integration.ElementHost> formantu o nazwie `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="38c79-135">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

3. <span data-ttu-id="38c79-136">W panelu tagi inteligentne dla `elementHost1`, otwórz **zaznacz hostowana zawartość** listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="38c79-136">In the smart tag panel for `elementHost1`, open the **Select Hosted Content** drop-down list.</span></span>

4. <span data-ttu-id="38c79-137">Wybierz **UserControl2** w polu listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="38c79-137">Select **UserControl2** from the drop-down list box.</span></span>

     <span data-ttu-id="38c79-138">`elementHost1` Kontroli teraz udostępnia wystąpienie `UserControl2` typu.</span><span class="sxs-lookup"><span data-stu-id="38c79-138">The `elementHost1` control now hosts an instance of the `UserControl2` type.</span></span>

5. <span data-ttu-id="38c79-139">W **właściwości** okna, upewnij się, że <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> właściwość jest ustawiona na **UserControl2**.</span><span class="sxs-lookup"><span data-stu-id="38c79-139">In the **Properties** window, confirm that the <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl2**.</span></span>

6. <span data-ttu-id="38c79-140">Z **przybornika**w **współdziałanie WPF** grupy, przeciągnij <xref:System.Windows.Forms.Integration.ElementHost> formant na formularzu.</span><span class="sxs-lookup"><span data-stu-id="38c79-140">From the **Toolbox**, in the **WPF Interoperability** group, drag an <xref:System.Windows.Forms.Integration.ElementHost> control onto the form.</span></span>

     <span data-ttu-id="38c79-141">Domyślna nazwa dla nowego formantu to `elementHost2`.</span><span class="sxs-lookup"><span data-stu-id="38c79-141">The default name for the new control is `elementHost2`.</span></span>

7. <span data-ttu-id="38c79-142">W panelu tagi inteligentne dla `elementHost2`, otwórz **zaznacz hostowana zawartość** listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="38c79-142">In the smart tag panel for `elementHost2`, open the **Select Hosted Content** drop-down list.</span></span>

8. <span data-ttu-id="38c79-143">Wybierz **UserControl1** z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="38c79-143">Select **UserControl1** from the drop-down list.</span></span>

9. <span data-ttu-id="38c79-144">`elementHost2` Kontroli teraz udostępnia wystąpienie `UserControl1` typu.</span><span class="sxs-lookup"><span data-stu-id="38c79-144">The `elementHost2` control now hosts an instance of the `UserControl1` type.</span></span>

## <a name="see-also"></a><span data-ttu-id="38c79-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38c79-145">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="38c79-146">Migracja i współdziałanie</span><span class="sxs-lookup"><span data-stu-id="38c79-146">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="38c79-147">Korzystanie z kontrolek WPF</span><span class="sxs-lookup"><span data-stu-id="38c79-147">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="38c79-148">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="38c79-148">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
