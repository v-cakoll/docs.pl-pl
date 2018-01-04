---
title: "Jak włączyć style Visual w aplikacji hybrydowej"
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
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- visual styles [Windows Forms]
ms.assetid: 95de9b9c-d804-405c-b2d1-49a88c1e0fe1
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 73f611eab7f75d1578652a8a9f5bb05d9720e851
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-visual-styles-in-a-hybrid-application"></a><span data-ttu-id="f7335-102">Jak włączyć style Visual w aplikacji hybrydowej</span><span class="sxs-lookup"><span data-stu-id="f7335-102">How to: Enable Visual Styles in a Hybrid Application</span></span>
<span data-ttu-id="f7335-103">W tym temacie przedstawiono sposób włączania [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] visual style na [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] kontroli hostowanych w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]— na podstawie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f7335-103">This topic shows how to enable [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] visual styles on a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control hosted in a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>  
  
 <span data-ttu-id="f7335-104">Jeśli aplikacja wymaga <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metody, większość z [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] formanty będą automatycznie używać stylów wizualnych, gdy aplikacja jest uruchamiana na [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f7335-104">If your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method, most of your [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls will automatically use visual styles when your application is run on [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)].</span></span> <span data-ttu-id="f7335-105">Aby uzyskać więcej informacji, zobacz [renderowanie formantów przy użyciu stylów wizualnych](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md).</span><span class="sxs-lookup"><span data-stu-id="f7335-105">For more information, see [Rendering Controls with Visual Styles](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md).</span></span>  
  
 <span data-ttu-id="f7335-106">Kompletny kod listę zadań przedstawione w tym temacie, można znaleźć [włączenie style wizualne w przykładowej aplikacji hybrydowych](http://go.microsoft.com/fwlink/?LinkID=159986).</span><span class="sxs-lookup"><span data-stu-id="f7335-106">For a complete code listing of the tasks illustrated in this topic, see [Enabling Visual Styles in a Hybrid Application Sample](http://go.microsoft.com/fwlink/?LinkID=159986).</span></span>  
  
## <a name="enabling-windows-forms-visual-styles"></a><span data-ttu-id="f7335-107">Włączanie Windows Forms style wizualne</span><span class="sxs-lookup"><span data-stu-id="f7335-107">Enabling Windows Forms Visual Styles</span></span>  
  
#### <a name="to-enable-windows-forms-visual-styles"></a><span data-ttu-id="f7335-108">Aby włączyć style wizualne formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f7335-108">To enable Windows Forms visual styles</span></span>  
  
1.  <span data-ttu-id="f7335-109">Utwórz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] projekt aplikacji o nazwie `HostingWfWithVisualStyles`.</span><span class="sxs-lookup"><span data-stu-id="f7335-109">Create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Application project named `HostingWfWithVisualStyles`.</span></span>  
  
2.  <span data-ttu-id="f7335-110">W Eksploratorze rozwiązań Dodaj odwołania do następujących zestawów.</span><span class="sxs-lookup"><span data-stu-id="f7335-110">In Solution Explorer, add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="f7335-111">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="f7335-111">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="f7335-112">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="f7335-112">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="f7335-113">Przybornik, kliknij dwukrotnie <xref:System.Windows.Controls.Grid> ikonę, aby umieścić <xref:System.Windows.Controls.Grid> elementu na powierzchnię projektu.</span><span class="sxs-lookup"><span data-stu-id="f7335-113">In the Toolbox, double-click the <xref:System.Windows.Controls.Grid> icon to place a <xref:System.Windows.Controls.Grid> element on the design surface.</span></span>  
  
4.  <span data-ttu-id="f7335-114">W oknie właściwości można ustawić wartości właściwości <xref:System.Windows.FrameworkElement.Height%2A> i <xref:System.Windows.FrameworkElement.Width%2A> właściwości **automatycznie**.</span><span class="sxs-lookup"><span data-stu-id="f7335-114">In the Properties window, set the values of the <xref:System.Windows.FrameworkElement.Height%2A> and <xref:System.Windows.FrameworkElement.Width%2A> properties to **Auto**.</span></span>  
  
5.  <span data-ttu-id="f7335-115">W widoku projektu lub XAML, wybierz <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="f7335-115">In Design view or XAML view, select the <xref:System.Windows.Window>.</span></span>  
  
6.  <span data-ttu-id="f7335-116">Kliknij w oknie właściwości **zdarzenia** kartę.</span><span class="sxs-lookup"><span data-stu-id="f7335-116">In the Properties window, click the **Events** tab.</span></span>  
  
7.  <span data-ttu-id="f7335-117">Kliknij dwukrotnie <xref:System.Windows.FrameworkElement.Loaded> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f7335-117">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>
  
8.  <span data-ttu-id="f7335-118">W MainWindow.xaml.vb lub MainWindow.xaml.cs, Wstaw następujący kod, aby obsłużyć <xref:System.Windows.FrameworkElement.Loaded> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f7335-118">In MainWindow.xaml.vb or MainWindow.xaml.cs, insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>  
  
     [!code-csharp[HostingWfWithVisualStyles#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HostingWfWithVisualStyles/CSharp/HostingWfWithVisualStyles/Window1.xaml.cs#11)]
     [!code-vb[HostingWfWithVisualStyles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfWithVisualStyles/VisualBasic/HostingWfWithVisualStyles/Window1.xaml.vb#11)]  
  
9. <span data-ttu-id="f7335-119">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="f7335-119">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="f7335-120">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Kontroli jest rysowane przy użyciu stylów wizualnych.</span><span class="sxs-lookup"><span data-stu-id="f7335-120">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is painted with visual styles.</span></span>  
  
## <a name="disabling-windows-forms-visual-styles"></a><span data-ttu-id="f7335-121">Wyłączanie Windows Forms style wizualne</span><span class="sxs-lookup"><span data-stu-id="f7335-121">Disabling Windows Forms Visual Styles</span></span>  
 <span data-ttu-id="f7335-122">Aby wyłączyć stylów wizualnych, po prostu usuń wywołanie <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f7335-122">To disable visual styles, simply remove the call to the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>  
  
#### <a name="to-disable-windows-forms-visual-styles"></a><span data-ttu-id="f7335-123">Aby wyłączyć style wizualne formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f7335-123">To disable Windows Forms visual styles</span></span>  
  
1.  <span data-ttu-id="f7335-124">Otwórz MainWindow.xaml.vb lub MainWindow.xaml.cs w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="f7335-124">Open MainWindow.xaml.vb or MainWindow.xaml.cs in the Code Editor.</span></span>  
  
2.  <span data-ttu-id="f7335-125">Komentarz wywołanie <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f7335-125">Comment out the call to the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>  
  
3.  <span data-ttu-id="f7335-126">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="f7335-126">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="f7335-127">[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Kontroli jest rysowane przy użyciu domyślnego systemu stylu.</span><span class="sxs-lookup"><span data-stu-id="f7335-127">The [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control is painted with the default system style.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7335-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f7335-128">See Also</span></span>  
 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>  
 <xref:System.Windows.Forms.VisualStyles>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="f7335-129">Renderowanie kontrolek przy użyciu stylów wizualnych</span><span class="sxs-lookup"><span data-stu-id="f7335-129">Rendering Controls with Visual Styles</span></span>](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 [<span data-ttu-id="f7335-130">Przewodnik: hosting kontrolki Windows Forms w WPF</span><span class="sxs-lookup"><span data-stu-id="f7335-130">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
