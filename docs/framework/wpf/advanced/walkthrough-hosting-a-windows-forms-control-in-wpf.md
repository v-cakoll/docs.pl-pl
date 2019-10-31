---
title: 'Wskazówki: hosting formantu Windows Forms w WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: 3cd01126e22927151f3c7fb08726c006c710dd34
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197925"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a><span data-ttu-id="678a6-102">Wskazówki: hosting formantu Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="678a6-102">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="678a6-103">udostępnia wiele kontrolek z bogatym zestawem funkcji.</span><span class="sxs-lookup"><span data-stu-id="678a6-103">provides many controls with a rich feature set.</span></span> <span data-ttu-id="678a6-104">Czasami jednak może być konieczne użycie formantów [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] na stronach [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="678a6-104">However, you may sometimes want to use [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="678a6-105">Na przykład możesz mieć znaczną inwestycję w istniejące kontrolki [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] lub mieć kontrolkę [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], która zapewnia unikalne funkcje.</span><span class="sxs-lookup"><span data-stu-id="678a6-105">For example, you may have a substantial investment in existing [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls, or you may have a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control that provides unique functionality.</span></span>

<span data-ttu-id="678a6-106">W tym instruktażu pokazano, jak hostować [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontrolę <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> na stronie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="678a6-106">This walkthrough shows you how to host a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using code.</span></span>

<span data-ttu-id="678a6-107">Aby zapoznać się z pełną listą zadań przedstawionych w tym instruktażu, zobacz [Hostowanie formantu Windows Forms w przykładzie WPF](https://go.microsoft.com/fwlink/?LinkID=160057).</span><span class="sxs-lookup"><span data-stu-id="678a6-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=160057).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="678a6-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="678a6-108">Prerequisites</span></span>

<span data-ttu-id="678a6-109">Aby ukończyć ten przewodnik, potrzebujesz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="678a6-109">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="678a6-110">Hostowanie kontrolki Windows Forms</span><span class="sxs-lookup"><span data-stu-id="678a6-110">Hosting the Windows Forms Control</span></span>

### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="678a6-111">Aby hostować formant formantem MaskedTextBox</span><span class="sxs-lookup"><span data-stu-id="678a6-111">To host the MaskedTextBox control</span></span>

1. <span data-ttu-id="678a6-112">Utwórz projekt aplikacji WPF o nazwie `HostingWfInWpf`.</span><span class="sxs-lookup"><span data-stu-id="678a6-112">Create a WPF Application project named `HostingWfInWpf`.</span></span>

2. <span data-ttu-id="678a6-113">Dodaj odwołania do następujących zestawów.</span><span class="sxs-lookup"><span data-stu-id="678a6-113">Add references to the following assemblies.</span></span>

    - <span data-ttu-id="678a6-114">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="678a6-114">WindowsFormsIntegration</span></span>

    - <span data-ttu-id="678a6-115">System. Windows. Forms</span><span class="sxs-lookup"><span data-stu-id="678a6-115">System.Windows.Forms</span></span>

3. <span data-ttu-id="678a6-116">Otwórz MainWindow. XAML w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="678a6-116">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>

4. <span data-ttu-id="678a6-117">Nadaj nazwę elementowi <xref:System.Windows.Controls.Grid> `grid1`.</span><span class="sxs-lookup"><span data-stu-id="678a6-117">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>

     [!code-xaml[HostingWfInWPF#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5. <span data-ttu-id="678a6-118">W widoku widok Projekt lub XAML wybierz element <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="678a6-118">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

6. <span data-ttu-id="678a6-119">W okno Właściwości kliknij kartę **zdarzenia** .</span><span class="sxs-lookup"><span data-stu-id="678a6-119">In the Properties window, click the **Events** tab.</span></span>

7. <span data-ttu-id="678a6-120">Kliknij dwukrotnie zdarzenie <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="678a6-120">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

8. <span data-ttu-id="678a6-121">Wstaw poniższy kod, aby obsłużyć zdarzenie <xref:System.Windows.FrameworkElement.Loaded>.</span><span class="sxs-lookup"><span data-stu-id="678a6-121">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

     [!code-csharp[HostingWfInWPF#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]

9. <span data-ttu-id="678a6-122">W górnej części pliku Dodaj następującą instrukcję `Imports` lub `using`.</span><span class="sxs-lookup"><span data-stu-id="678a6-122">At the top of the file, add the following `Imports` or `using` statement.</span></span>

     [!code-csharp[HostingWfInWPF#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]

10. <span data-ttu-id="678a6-123">Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="678a6-123">Press **F5** to build and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="678a6-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="678a6-124">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="678a6-125">Projektowanie XAML w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="678a6-125">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [<span data-ttu-id="678a6-126">Przewodnik: hosting kontrolki Windows Form w WPF z wykorzystaniem XAML</span><span class="sxs-lookup"><span data-stu-id="678a6-126">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)
- [<span data-ttu-id="678a6-127">Przewodnik: hosting złożonej kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="678a6-127">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="678a6-128">Przewodnik: hosting złożonej kontrolki WPF w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="678a6-128">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="678a6-129">Kontrolki formularzy Windows Forms i równoważne kontrolki WPF</span><span class="sxs-lookup"><span data-stu-id="678a6-129">Windows Forms Controls and Equivalent WPF Controls</span></span>](windows-forms-controls-and-equivalent-wpf-controls.md)
- [<span data-ttu-id="678a6-130">Hostowanie kontrolki Windows Forms w przykładzie WPF</span><span class="sxs-lookup"><span data-stu-id="678a6-130">Hosting a Windows Forms Control in WPF Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160057)
