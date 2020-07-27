---
title: Hostowanie kontrolki Windows Forms w WPF
description: Dowiedz się, jak hostować Windows Forms formantów w Windows Presentation Foundation, które już udostępniają wiele kontrolek z bogatym zestawem funkcji.
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: ec67cf9fabaa5b7aadbb2a3c21ebf8dd828ee20f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164977"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a><span data-ttu-id="23b05-103">Przewodnik: hostowanie kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="23b05-103">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="23b05-104">oferuje wiele kontrolek z bogatym zestawem funkcji.</span><span class="sxs-lookup"><span data-stu-id="23b05-104">provides many controls with a rich feature set.</span></span> <span data-ttu-id="23b05-105">Czasami jednak może być konieczne użycie formantów Windows Forms na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stronach.</span><span class="sxs-lookup"><span data-stu-id="23b05-105">However, you may sometimes want to use Windows Forms controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="23b05-106">Na przykład możesz mieć znaczną inwestycję w istniejące kontrolki Windows Forms lub mieć kontrolkę Windows Forms, która zapewnia unikalne funkcje.</span><span class="sxs-lookup"><span data-stu-id="23b05-106">For example, you may have a substantial investment in existing Windows Forms controls, or you may have a Windows Forms control that provides unique functionality.</span></span>

<span data-ttu-id="23b05-107">W tym instruktażu pokazano, jak hostować <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> formant Windows Forms na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stronie przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="23b05-107">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using code.</span></span>

<span data-ttu-id="23b05-108">Aby zapoznać się z pełną listą zadań przedstawionych w tym instruktażu, zobacz [Hostowanie formantu Windows Forms w przykładzie WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF).</span><span class="sxs-lookup"><span data-stu-id="23b05-108">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="23b05-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="23b05-109">Prerequisites</span></span>

<span data-ttu-id="23b05-110">Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="23b05-110">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="23b05-111">Hostowanie kontrolki Windows Forms</span><span class="sxs-lookup"><span data-stu-id="23b05-111">Hosting the Windows Forms Control</span></span>

### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="23b05-112">Aby hostować formant formantem MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="23b05-112">To host the MaskedTextBox control</span></span>

1. <span data-ttu-id="23b05-113">Utwórz projekt aplikacji WPF o nazwie `HostingWfInWpf` .</span><span class="sxs-lookup"><span data-stu-id="23b05-113">Create a WPF Application project named `HostingWfInWpf`.</span></span>

2. <span data-ttu-id="23b05-114">Dodaj odwołania do następujących zestawów.</span><span class="sxs-lookup"><span data-stu-id="23b05-114">Add references to the following assemblies.</span></span>

    - <span data-ttu-id="23b05-115">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="23b05-115">WindowsFormsIntegration</span></span>

    - <span data-ttu-id="23b05-116">System. Windows. Forms</span><span class="sxs-lookup"><span data-stu-id="23b05-116">System.Windows.Forms</span></span>

3. <span data-ttu-id="23b05-117">Otwórz MainWindow. XAML w projektancie WPF.</span><span class="sxs-lookup"><span data-stu-id="23b05-117">Open MainWindow.xaml in the WPF Designer.</span></span>

4. <span data-ttu-id="23b05-118">Nadaj nazwę <xref:System.Windows.Controls.Grid> element `grid1` .</span><span class="sxs-lookup"><span data-stu-id="23b05-118">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>

     [!code-xaml[HostingWfInWPF#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5. <span data-ttu-id="23b05-119">W widoku widok Projekt lub XAML wybierz <xref:System.Windows.Window> element.</span><span class="sxs-lookup"><span data-stu-id="23b05-119">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

6. <span data-ttu-id="23b05-120">W okno Właściwości kliknij kartę **zdarzenia** .</span><span class="sxs-lookup"><span data-stu-id="23b05-120">In the Properties window, click the **Events** tab.</span></span>

7. <span data-ttu-id="23b05-121">Kliknij dwukrotnie <xref:System.Windows.FrameworkElement.Loaded> zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="23b05-121">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

8. <span data-ttu-id="23b05-122">Wstaw następujący kod, aby obsłużyć <xref:System.Windows.FrameworkElement.Loaded> zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="23b05-122">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

     [!code-csharp[HostingWfInWPF#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]

9. <span data-ttu-id="23b05-123">W górnej części pliku Dodaj następującą `Imports` `using` instrukcję lub.</span><span class="sxs-lookup"><span data-stu-id="23b05-123">At the top of the file, add the following `Imports` or `using` statement.</span></span>

     [!code-csharp[HostingWfInWPF#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]

10. <span data-ttu-id="23b05-124">Naciśnij klawisz **F5**, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="23b05-124">Press **F5** to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="23b05-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23b05-125">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="23b05-126">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="23b05-126">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="23b05-127">Przewodnik: hostowanie kontrolki Windows Forms w WPF z wykorzystaniem języka XAML</span><span class="sxs-lookup"><span data-stu-id="23b05-127">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)
- [<span data-ttu-id="23b05-128">Przewodnik: hostowanie kontrolki złożonej Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="23b05-128">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="23b05-129">Przewodnik: hostowanie kontrolki złożonej WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="23b05-129">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="23b05-130">Kontrolki Windows Forms i ekwiwalentne kontrolki WPF</span><span class="sxs-lookup"><span data-stu-id="23b05-130">Windows Forms Controls and Equivalent WPF Controls</span></span>](windows-forms-controls-and-equivalent-wpf-controls.md)
- [<span data-ttu-id="23b05-131">Hostowanie kontrolki Windows Forms w przykładzie WPF</span><span class="sxs-lookup"><span data-stu-id="23b05-131">Hosting a Windows Forms Control in WPF Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/HostingWfInWPF)
