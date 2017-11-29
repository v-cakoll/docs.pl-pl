---
title: "Wskazówki: hosting formantu Windows Forms w WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 71c48b85af6767d59eaa68621faf566321af613c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a><span data-ttu-id="c1000-102">Wskazówki: hosting formantu Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="c1000-102">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="c1000-103">udostępnia wiele formantów z zestawem funkcji zaawansowanych.</span><span class="sxs-lookup"><span data-stu-id="c1000-103"> provides many controls with a rich feature set.</span></span> <span data-ttu-id="c1000-104">Jednak czasami warto użyć [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów w Twojej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stron.</span><span class="sxs-lookup"><span data-stu-id="c1000-104">However, you may sometimes want to use [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="c1000-105">Na przykład może mieć znaczne inwestycji w istniejących [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formantów, lub może być [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formant, który udostępnia funkcje unikatowy.</span><span class="sxs-lookup"><span data-stu-id="c1000-105">For example, you may have a substantial investment in existing [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls, or you may have a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control that provides unique functionality.</span></span>  
  
 <span data-ttu-id="c1000-106">W tym przewodniku przedstawiono sposób obsługi [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> kontrolować na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] strony przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="c1000-106">This walkthrough shows you how to host a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]<xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using code.</span></span>  
  
 <span data-ttu-id="c1000-107">Kompletny kod lista zadań wyświetlane w tym przewodniku, zobacz [hostowanie kontrolki formularza systemu Windows w przykładowym WPF](http://go.microsoft.com/fwlink/?LinkID=160057).</span><span class="sxs-lookup"><span data-stu-id="c1000-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF Sample](http://go.microsoft.com/fwlink/?LinkID=160057).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c1000-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="c1000-108">Prerequisites</span></span>  
 <span data-ttu-id="c1000-109">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="c1000-109">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="c1000-110">.</span><span class="sxs-lookup"><span data-stu-id="c1000-110">.</span></span>  
  
## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="c1000-111">Hostowanie kontrolki formularza systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c1000-111">Hosting the Windows Forms Control</span></span>  
  
#### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="c1000-112">Na hoście maskedtextbox — formant</span><span class="sxs-lookup"><span data-stu-id="c1000-112">To host the MaskedTextBox control</span></span>  
  
1.  <span data-ttu-id="c1000-113">Utwórz projekt aplikacji WPF o nazwie `HostingWfInWpf`.</span><span class="sxs-lookup"><span data-stu-id="c1000-113">Create a WPF Application project named `HostingWfInWpf`.</span></span>  
  
2.  <span data-ttu-id="c1000-114">Dodaj odwołania do następujących zestawów.</span><span class="sxs-lookup"><span data-stu-id="c1000-114">Add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="c1000-115">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="c1000-115">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="c1000-116">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="c1000-116">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="c1000-117">Otwórz MainWindow.xaml w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c1000-117">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="c1000-118">Nazwa <xref:System.Windows.Controls.Grid> elementu `grid1`.</span><span class="sxs-lookup"><span data-stu-id="c1000-118">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>  
  
     [!code-xaml[HostingWfInWPF#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]  
  
5.  <span data-ttu-id="c1000-119">W widoku projektu lub XAML, wybierz <xref:System.Windows.Window> elementu.</span><span class="sxs-lookup"><span data-stu-id="c1000-119">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>  
  
6.  <span data-ttu-id="c1000-120">Kliknij w oknie właściwości **zdarzenia** kartę.</span><span class="sxs-lookup"><span data-stu-id="c1000-120">In the Properties window, click the **Events** tab.</span></span>  
  
7.  <span data-ttu-id="c1000-121">Kliknij dwukrotnie <xref:System.Windows.FrameworkElement.Loaded> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c1000-121">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
8.  <span data-ttu-id="c1000-122">Wstaw następujący kod, aby obsłużyć <xref:System.Windows.FrameworkElement.Loaded> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c1000-122">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
     [!code-csharp[HostingWfInWPF#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]  
  
9. <span data-ttu-id="c1000-123">W górnej części pliku, Dodaj następujący `Imports` lub `using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c1000-123">At the top of the file, add the following `Imports` or `using` statement.</span></span>  
  
     [!code-csharp[HostingWfInWPF#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]  
  
10. <span data-ttu-id="c1000-124">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="c1000-124">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1000-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1000-125">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="c1000-126">Projektant WPF</span><span class="sxs-lookup"><span data-stu-id="c1000-126">WPF Designer</span></span>](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 [<span data-ttu-id="c1000-127">Wskazówki: Hostowanie kontrolki formularza systemu Windows na platformie WPF przy użyciu języka XAML</span><span class="sxs-lookup"><span data-stu-id="c1000-127">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)  
 [<span data-ttu-id="c1000-128">Wskazówki: Obsługa formantu złożonego formularzy systemu Windows na platformie WPF</span><span class="sxs-lookup"><span data-stu-id="c1000-128">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [<span data-ttu-id="c1000-129">Wskazówki: Hostowanie formantu złożonego WPF w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c1000-129">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [<span data-ttu-id="c1000-130">Formanty i równoważne WPF formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c1000-130">Windows Forms Controls and Equivalent WPF Controls</span></span>](../../../../docs/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls.md)  
 [<span data-ttu-id="c1000-131">Hostowanie kontrolki formularza systemu Windows w przykładowym WPF</span><span class="sxs-lookup"><span data-stu-id="c1000-131">Hosting a Windows Forms Control in WPF Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160057)
